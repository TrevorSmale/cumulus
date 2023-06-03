---
title: "Cron"
date: 2023-05-29T18:31:10-04:00
draft: false
---

{{< panel title="Update Log" style="success" >}}

* 2023 06 02 - Initial Commit

{{< /panel >}}

{{< lead >}}

## Overview

UNIX cron is a time-based job scheduling system used in UNIX-like operating systems to automate recurring tasks or jobs. It allows users to schedule commands or scripts to run at specific intervals, such as minutes, hours, days, or months. Cron jobs are created and managed using the cron daemon.

Here are some key components and concepts related to UNIX cron:

* Crontab: The cron table, commonly referred to as crontab, is a file that stores the list of cron jobs and their schedules. Each user on a system can have their own crontab file.

* Cron Schedule: A cron schedule consists of fields representing different time units, such as minutes, hours, days of the month, months, and days of the week. By specifying values in these fields, users can define when a cron job should execute.

* Cron Jobs: A cron job is a command or script that is scheduled to run at a specified time according to the cron schedule. It can perform various tasks, such as running scripts, executing commands, or triggering system actions.

* Cron Daemon: The cron daemon is a background process that constantly checks the cron tables to determine if any jobs are scheduled to run. It initiates the execution of the specified commands or scripts based on the defined schedules.

To create or edit cron jobs, users typically use the crontab command to modify their crontab file. The syntax for defining a cron job in the crontab file is as follows:
Cron is a tas

{{< /lead >}}

## Troubleshooting

* NOTE: `echo` won't work because `cron` runs in its own shell.

## Possible problems:

{{< panel title="" style="danger" >}}

### 1. Not using absolute paths

    /bin/echo "cron works" >> /tmp/file

---

### 2. Not using a PATH variable

    PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

    echo "cron works" >> /tmp/file

---

### 3. Not escaping characters

    mysqldump --databases db > /home/user/backup-$(date +%Y%m%d-%H%M%S)
    mysqldump --databases db > /home/user/backup-$(date +\%Y\%m\%d-\%H\%M\%S)

---

### 4. Not leaving an empty new line in the end

{{< /panel >}}

## Cron Tab

Each user has his own crontab i.e. cron table i.e table of scheduled processes.

    List

    # list of tasks for current user
    crontab -l

    # list of tasks for specific user
    crontab –u username –l

---

### Edit

#### edit crontabs for current user
    crontab -e

#### edit tasks for specific user
    crontab –u username –e

#### edit tasks for root user
    sudo crontab -e


---

### Jobs

#### list of crontabs
    sudo less /var/spool/cron/crontabs

#### root systemwide crontab
    sudo less /etc/crontab

---

## Format

{{< panel title="" style="info" >}}

**NOTE: Cron doesn't do seconds. Minimum is every minute.**


    .---------------- minute (0 - 59)
    |  .------------- hour (0 - 23)
    |  |  .---------- day of month (1 - 31)
    |  |  |  .------- month (1 - 12) OR jan, feb, mar, apr...
    |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun, mon, tue, wed, thu, fri, sat
    |  |  |  |  |
    *  *  *  *  * command to be executed

    *     all
    ,     list of values
    x-y   range of values
    /x    recurring i.e. every x times

{{< /panel >}}

**NOTE: The timing doesn't overlap, meaning it happens in both cases, not a combination of the two.**


### Every minute
    * * * * *

---

### Every hour
    0 * * * *

---

### Every 2 hours
    0 */2 * * *

---

### Every day @ 23:59
    59 23 * * *

---

### Sunday @ 23:59
    59 23 * * 0

---

### At every minute past every hour from 7 through 18 on every day-of-week from Monday through Friday
    * 7-18 * * 1-5

---

### At every 20th minute past hour 22 on day-of-month 1 and 15
    */20 22 1,15 * *

---

### At 10:15 on every 2nd day-of-month from 1 through 10 and on Friday
    15 10 1-10/2 * 5

