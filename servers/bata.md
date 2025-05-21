## Scenario: "Bata": Find in /proc

### Level: Easy

### Description

A spy has left a password in a file in /proc/sys . The contents of the file start with "secret:" (without the quotes).

Find the file and save the word after "secret:" to the file /home/admin/secret.txt with a newline at the end (e.g. if the file contents were "secret:password" do: echo "password" > /home/admin/secret.txt).

(Note there's no root/sudo access in this scenario).

### Test 

Running md5sum /home/admin/secret.txt returns a7fcfd21da428dd7d4c5bb4c2e2207c4

The "Check My Solution" button runs the script /home/admin/agent/check.sh, which you can see and execute.

Time to Solve: 10 minutes.

OS: Debian 11

Root (sudo) Access: No

### Solution
To find the file in `/proc/sys`, I can use the `grep` command to search for the string

```bash
grep -Ri "secret:" /proc/sys
```

Found that the password is "excalibur" then append it to the file `/home/admin/secret.txt` with a new line at the end.

```bash
echo "excalibur" >> /home/admin/secret.txt
```

### Completed challenge

![complete](../images/bata.png)