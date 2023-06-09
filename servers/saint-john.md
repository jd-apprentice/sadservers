## "Saint John": what is writing to this log file?

### Problem

Scenario: "Saint John": what is writing to this log file?

Level: Easy

Description: A developer created a testing program that is continuously writing to a log file /var/log/bad.log and filling up disk. You can check for example with tail -f /var/log/bad.log.
This program is no longer needed. Find it and terminate it.

Test: The log file hasn't changed in the last 6 seconds: find /var/log/bad.log -mmin -0.1 (You don't need to know the details of this command).

Time to Solve: 10 minutes.

OS: Ubuntu 22.04 LTS

### Solution

I've used the following command to find the process that is writing to the log file:

```bash
$ ps aux | grep python
```

With this command I've got 3 processes that are uusing python at the moment, but only one was the culprit

At first I went to home and search for the .python_history and get a clue about the file that was writing to the log file

A file named `badlog.py` was writing to the log file

At first I tried to rm the file but it would keep running, so I've killed the process with the following command:

```bash
$ kill <process_id>
```

### Completed challenge

- Amount of times required to solve: 2
- Clues used: 0

![COMPLETE](../images/saint.png)