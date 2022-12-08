## Part 1
        sudo apt update
        sudo apt upgrade

## Part 2
x - delete a character 
(V -> C)
(numbs -> :digit:)

## Part 4
        #!/bin/bash

        echo "Regular usrs on the system are:"

        grep -E '\b(100[0-9]|5000)\b' /etc/passwd
        user1="$(grep -E '\b(100[0-9]|5000)\b' /etc/passwd | awk 'NR==1{print$1}')"
        user2="$(grep -E '\b(100[0-9]|5000)\b' /etc/passwd | awk 'NR==1{print$1}')"
        #user1="$(grep -E '\b(100[0-9]|5000)\b' /etc/passwd | awk 'NR==1{print$1}')"
        #user1="$(grep -E '\b(100[0-9]|5000)\b' /etc/passwd | awk 'NR==1{print$1}')"

        echo "Users currently logged in are:"
        who

## Part 5
        sudo vim /etc/systemd/system/find_users.service

        [Unit]
        Description =list regular users
        After = network.target

        [Service]
        ExecStart =/home/user1/find_users

        [Install]
        WantedBy = multi-user.target

        systemctl enable find_users.service
        systemctl start find_users.service
        systemctl status find_users.service