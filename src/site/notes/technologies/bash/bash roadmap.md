---
{"dg-publish":true,"permalink":"/technologies/bash/bash-roadmap/","dg-note-properties":{}}
---

#bash

for **Linux, Docker, Big Data, cloud, security, and #hpc 

---

## Must know before S 7

| Topic           | What you should know                            |
| --------------- | ----------------------------------------------- |
| Navigation      | `pwd`, `ls`, `cd`, `mkdir`, `rm`, `cp`, `mv`    |
| Files           | `cat`, `less`, `head`, `tail`, `touch`, `chmod` |
| Search          | `grep`, `find`, `locate`                        |
| Pipes           | `                                               |
| Permissions     | `chmod`, `chown`, `sudo`                        |
| Processes       | `ps`, `top`/`htop`, `kill`, background jobs     |
| Environment     | `PATH`, `export`, `.bashrc`                     |
| Packages        | `apt update`, `apt install` on Linux Mint       |
| Python setup    | `python3 -m venv`, `pip`, `requirements.txt`    |
| Basic scripting | Variables, loops, `if`, functions               |

---

## Useful before Semesters 8 and 9

| Topic           | Why                                         |
| --------------- | ------------------------------------------- |
| SSH             | Connect to servers, run remote commands     |
| `scp` / `rsync` | Transfer files to servers/clusters          |
| `tar`, `zip`    | Archive datasets and models                 |
| `curl` / `wget` | Download datasets, models, APIs             |
| Docker CLI      | Run Hadoop, Spark, Kafka, distributed tools |
| Logs            | `journalctl`, `tail -f`, debugging services |
| Cron/systemd    | Automate scripts and services               |
| `awk` / `sed`   | Quick text/data processing                  |
| Process control | Run long training jobs, nohup, screen/tmux  |

---

## Concepts learned through courses

| Course                           | Bash usage                                                            |
| -------------------------------- | --------------------------------------------------------------------- |
| High-Performance Computing       | Compile/run C programs, Slurm job scripts, profiling, SSH to clusters |
| Big Data                         | Start/stop Hadoop, HDFS commands, Spark submit, Docker cluster setup  |
| Distributed Computing            | Cloud/edge server setup, Docker, SSH, container management            |
| Security                         | File permissions, log analysis, network tools, exploit labs           |
| Machine Learning / Deep Learning | Run training scripts, manage environments, download datasets/models   |
| Project                          | Automate build/run/test/deploy steps                                  |

---

## Minimum Bash checklist

You should know these commands:

```bash
ls -la
cd folder
mkdir project
cp file.txt backup/
mv old.txt new.txt
rm -r folder
grep "error" log.txt
find . -name "*.py"
chmod +x script.sh
./script.sh
```

Basic script:

```bash
#!/usr/bin/env bash
set -euo pipefail

echo "Starting setup"

for file in *.csv; do
    echo "Processing $file"
done

echo "Done"
```

Run:

```bash
chmod +x script.sh
./script.sh
```

---

Before  7: learn **[[technologies/bash/Linux navigation\|Linux navigation]], [[technologies/bash/permissions\|permissions]], pipes, grep/find, basic scripts, apt, and Python virtual environments**.

later: mostly **Docker, Hadoop/Spark, SSH, logs, automation, and running long training jobs**.