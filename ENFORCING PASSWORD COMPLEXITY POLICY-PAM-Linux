PAM is an acronym for Pluggable Authentication Module. This is a framework that is used to control authentication and authorization in most Unix systems.

There are different authentication sources that can be used in Unix systems supports. For example, using SSSD, Kerberos or even the most common local authentication. For each authentication source, there is a PAM module that can be used.

# ENFORCING PASSWORD COMPLEXITY POLICY
The pam_pwquality.so is a PAM module that is used to check the password quality against a set of rules. This module has replaced the pam_cracklib that was used in RHEL 6 and its derivatives.

## The pam_pwquality.so follows two steps in verifying the strength of the password. When setting password:

* It first checks the provided password is a dictionary password. If not, it continues to check the password against the set rules, such as
      
      Palindrome - Is the new password a palindrome?
      Case Change Only - Is the new password the old one with only a change of case?
      Similar - Is the new password too much like the old one?
      Simple - Is the new password too small?
      Rotated - Is the new password a rotated version of the old password?
      Same consecutive characters - Optional check for same consecutive characters.
      Contains user name - Optional, check whether the password contains the user name in some form.

2. If the password passes the checks and is considered strong enough, the user is prompted to re-enter the password after which is set.

These checks are configurable either by use of the module arguments or by modifying the /etc/security/pwquality.conf configuration file. Before you can start to modify the /etc/security/pwquality.conf ensure that you make a backup using the following command:

```bash 
cp /etc/security/pwquality.conf /etc/security/pwquality.conf.original
```

The changes can also be effected by modifying the /etc/pam.d/system-auth configuration file. Therefore, make a backup of this configuration file also using the command below:

```bash
cp /etc/pam.d/system-auth /etc/pam.d/system-auth.original
```
Next, open the /etc/pam.d/system-auth configuration file for editing.
```bash
vim /etc/pam.d/system-auth
```
Locate the line containing the pam_pwquality.so;

password requisite pam_pwquality.so try_first_pass local_users_only retry=3 authtok_type=.
This is the line that we are going to modify to implement our password complexity policy.
Among the password complexity options that we are going to use in this scenario include;

minlen=N - sets the minimum acceptable size for the new password to N characters.
lcredit=N - Sets the minimum number of lower case letters that the password should contain to at least one.
ucredit=N- Sets the minimum number of upper case letters on a password to at least one.
dcredit=N – Sets the minimum number of digits to be contained in a password to at least one
ocredit=N – Set the minimum number of other symbols such as @, #, ! $ % etc. on a password to at least one.
maxrepeat=N - Ensures that no more than N same consecutive characters that were in the old password appears on the new password.

enforce_for_root – Ensures that even if it is the root user that is setting the password, the complexity policies should be enforced.

For example, to enforce a password complexity policy that requires that any password to be set by the user should contain at least; - 15 characters (minlen=15) - one lower case letter (lcredit=-1) - one upper case letter (ucredit=-1) - one digit (dcredit=-1) - one symbol (ocredit=-1) - not more than 3 same consecutive characters in the old password appears on the new password (maxrepeat=3).

Modify the pam_pwquality.so line above such that it looks like;

password requisite pam_pwquality.so try_first_pass local_users_only retry=3 authtok_type= minlen=8 lcredit=-1 ucredit=-1 dcredit=-1 ocredit=-1 maxrepeat=3

If you are using the /etc/security/pwquality.conf, each of these options should be set each per line, such that they look like;

minlen = 15 maxrepeat = 3 lcredit = -1 ucredit = -1 dcredit = -1 ocredit = -1

Configuring Password Complexity in the Command Line

The /etc/security/pwquality.conf can also be updated using the authconfig utility from the command line.

For you to implement the above password complexity options using the authconfig command, simply run;

authconfig --enablereqlower --enablerequpper --enablereqdigit --enablereqother --passminlen=15 --passmaxrepeat=3 --update

Where;

--enablerequpper specifies the minimum number of uppercase letters

--enablereqlower specifies the minimum number of lowercase letters.

--enablereqdigit sets minimum number of digits.

--enablereqother sets the minimum number of other symbols.

--passmaxrepeat set the number of times a character can be repeated consecutively.

--passminlen sets the minimum length of the password.

--update this option updates the /etc/security/pwquality.conf configuration file.

Once the command runs, changes are appended to the end of the /etc/security/pwquality.conf file.

# TESTING PASSWORD ENFORCEMENT POLICY
As a non-root user, try to change the current password to a password that doesn’t meet the set complexity checks. In order to do this, use the passwd command.
```bash
[amos@cent7 ~]$ passwd Changing password for user amos. Changing password for amos. 
(current) UNIX password: 
New password: BAD PASSWORD: The password is too similar to the old one 
New password: BAD PASSWORD: The password is too similar to the old one New password:
Until when you enter a password that conforms to the complexity checks, the password can be reset. For example, the password like, MyP@ssw0rdNEwonE will work.

[amos@cent7 ~]$ passwd Changing password for user amos. Changing password for amos. 
(current) UNIX password: password 
New password: MyP@ssw0rdNEwonE 
Retype new password: MyP@ssw0rdNEwonE 
passwd: all authentication tokens updated successfully.
[amos@cent7 ~]$
```

# ENFORCING PASSWORD COMPLEXITY FOR ROOT USER

>[!NOTE] Note that the above changes can only apply to non-root user. If you try to change the password as root user or as user with sudo rights, the password can accept anything.

To ensure that the password complexity applies to anyone including privileged users, you need to add the option, enforce_for_root to the /etc/pam.d/system-auth configuration file.

For example, to enforce the above checks for the privileged user, add the line below to the /etc/pam.d/system-auth.

password requisite pam_pwquality.so try_first_pass local_users_only retry=3 authtok_type= minlen=8 lcredit=-1 ucredit=-1 dcredit=-1 ocredit=-1 maxrepeat=3 enforce_for_root

You can now test password complexity by using a simple password that doesn't conform to the checks implemented above and one that conforms.
```bash
[root@cent7 ~]# passwd amos 
Changing password for user amos. 
New password: BAD PASSWORD: The password contains less than 1 digits 
New password: BAD PASSWORD: The password is shorter than 15 characters 
New password: BAD PASSWORD: The password contains less than 1 uppercase letters 
passwd: Have exhausted maximum number of retries for service 
[root@cent7 ~]#
Using a password like, MyP@ssw0rdNEwonE will work.

[root@cent7 ~]# passwd amos 
Changing password for user amos. 
New password: MyP@ssw0rdNEwonE 
Retype new password: MyP@ssw0rdNEwonE 
passwd: all authentication tokens updated successfully. 
[root@cent7 ~]#
```

# DISABLE PASSWORD RE-USE USING pwhistory PAM MODULE

pam_pwhistory.so can be used to prevent users from reusing previous passwords. This module saves the last passwords for each user in order to force password change history and keep the user from alternating between the same password too frequently.

For example, to enforce a password history that prohibits the user from re-using four previous passwords, open the /etc/pam.d/system-auth configuration file using the command below:

vi /etc/pam.d/system-auth

Add the line below just after the first occurrence of password requisite line :

password requisite pam_pwhistory.so debug use_authtok remember=12 retry=3 enforce_for_root

The options used here are;

debug - which turns on debugging via syslog.

use_authok - tells the module to accept the password that the user inputs after it has passed through the checks.

remember - specifies the number of last passwords for each user to be remembered. The default is 10.

retry - specifies the number of times a user should be prompted for password before returning the error.

enforce_for_root - enforce the checks for the root user too.

To test this, try and reset the password for the user two times.

[root@cent7 ~]# passwd amos 
Changing password for user amos. 
New password: ruIcWocFufPhij#1 
Retype new password: ruIcWocFufPhij#1 
passwd: all authentication tokens updated successfully. 
[root@cent7 ~]#
On the second time, try to use the previous password. You should see a warning, Password has been already used. Choose another.

[root@cent7 ~]# passwd amos 
Changing password for user amos. 
New password: 
Retype new password: Password has been already used. Choose another. 
passwd: Authentication token manipulation error 
[root@cent7 ~]#

## Well, that is all on our scenario on how to enforce password complexity on CentOS 7.
