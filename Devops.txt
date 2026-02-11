# DevOps Commands Cheat Sheet

---

## Basic Linux Commands

> Linux is the foundation of DevOps operations - it's like a Swiss Army knife for servers. These commands help you navigate systems, manage files, configure permissions, and automate tasks in terminal environments.

| # | Command | Description |
|---|---------|-------------|
| 1 | `pwd` | Print the current working directory |
| 2 | `ls` | List files and directories |
| 3 | `cd` | Change directory |
| 4 | `touch` | Create an empty file |
| 5 | `mkdir` | Create a new directory |
| 6 | `rm` | Remove files or directories |
| 7 | `rmdir` | Remove empty directories |
| 8 | `cp` | Copy files or directories |
| 9 | `mv` | Move or rename files and directories |
| 10 | `cat` | Display the content of a file |
| 11 | `echo` | Display a line of text |
| 12 | `clear` | Clear the terminal screen |

---

## Intermediate Linux Commands

| # | Command | Description |
|---|---------|-------------|
| 13 | `chmod` | Change file permissions |
| 14 | `chown` | Change file ownership |
| 15 | `find` | Search for files and directories |
| 16 | `grep` | Search for text in a file |
| 17 | `wc` | Count lines, words, and characters in a file |
| 18 | `head` | Display the first few lines of a file |
| 19 | `tail` | Display the last few lines of a file |
| 20 | `sort` | Sort the contents of a file |
| 21 | `uniq` | Remove duplicate lines from a file |
| 22 | `diff` | Compare two files line by line |
| 23 | `tar` | Archive files into a tarball |
| 24 | `zip/unzip` | Compress and extract ZIP files |
| 25 | `df` | Display disk space usage |
| 26 | `du` | Display directory size |
| 27 | `top` | Monitor system processes in real time |
| 28 | `ps` | Display active processes |
| 29 | `kill` | Terminate a process by its PID |
| 30 | `ping` | Check network connectivity |
| 31 | `wget` | Download files from the internet |
| 32 | `curl` | Transfer data from or to a server |
| 33 | `scp` | Securely copy files between systems |
| 34 | `rsync` | Synchronize files and directories |

---

## Advanced Linux Commands

| # | Command | Description |
|---|---------|-------------|
| 35 | `awk` | Text processing and pattern scanning |
| 36 | `sed` | Stream editor for filtering and transforming text |
| 37 | `cut` | Remove sections from each line of a file |
| 38 | `tr` | Translate or delete characters |
| 39 | `xargs` | Build and execute command lines from standard input |
| 40 | `ln` | Create symbolic or hard links |
| 41 | `df -h` | Display disk usage in human-readable format |
| 42 | `free` | Display memory usage |
| 43 | `iostat` | Display CPU and I/O statistics |
| 44 | `netstat` | Network statistics (use `ss` as modern alternative) |
| 45 | `ifconfig/ip` | Configure network interfaces (use `ip` as modern alternative) |
| 46 | `iptables` | Configure firewall rules |
| 47 | `systemctl` | Control the systemd system and service manager |
| 48 | `journalctl` | View system logs |
| 49 | `crontab` | Schedule recurring tasks |
| 50 | `at` | Schedule tasks for a specific time |
| 51 | `uptime` | Display system uptime |
| 52 | `whoami` | Display the current user |
| 53 | `users` | List all users currently logged in |
| 54 | `hostname` | Display or set the system hostname |
| 55 | `env` | Display environment variables |
| 56 | `export` | Set environment variables |

---

## Networking Commands

| # | Command | Description |
|---|---------|-------------|
| 57 | `ip addr` | Display or configure IP addresses |
| 58 | `ip route` | Show or manipulate routing tables |
| 59 | `traceroute` | Trace the route packets take to a host |
| 60 | `nslookup` | Query DNS records |
| 61 | `dig` | Query DNS servers |
| 62 | `ssh` | Connect to a remote server via SSH |
| 63 | `ftp` | Transfer files using the FTP protocol |
| 64 | `nmap` | Network scanning and discovery |
| 65 | `telnet` | Communicate with remote hosts |
| 66 | `netcat (nc)` | Read/write data over networks |

---

## File Management and Search

| # | Command | Description |
|---|---------|-------------|
| 67 | `locate` | Find files quickly using a database |
| 68 | `stat` | Display detailed information about a file |
| 69 | `tree` | Display directories as a tree |
| 70 | `file` | Determine a file's type |
| 71 | `basename` | Extract the filename from a path |
| 72 | `dirname` | Extract the directory part of a path |

---

## System Monitoring

| # | Command | Description |
|---|---------|-------------|
| 73 | `vmstat` | Display virtual memory statistics |
| 74 | `htop` | Interactive process viewer (alternative to top) |
| 75 | `lsof` | List open files |
| 76 | `dmesg` | Print kernel ring buffer messages |
| 77 | `uptime` | Show how long the system has been running |
| 78 | `iotop` | Display real-time disk I/O by processes |

---

## Package Management

| # | Command | Description |
|---|---------|-------------|
| 79 | `apt` | Package manager for Debian-based distributions |
| 80 | `yum/dnf` | Package manager for RHEL-based distributions |
| 81 | `snap` | Manage snap packages |
| 82 | `rpm` | Manage RPM packages |

---

## Disk and Filesystem

| # | Command | Description |
|---|---------|-------------|
| 83 | `mount/umount` | Mount or unmount filesystems |
| 84 | `fsck` | Check and repair filesystems |
| 85 | `mkfs` | Create a new filesystem |
| 86 | `blkid` | Display information about block devices |
| 87 | `lsblk` | List information about block devices |
| 88 | `parted` | Manage partitions interactively |

---

## Scripting and Automation

| # | Command | Description |
|---|---------|-------------|
| 89 | `bash` | Command interpreter and scripting shell |
| 90 | `sh` | Legacy shell interpreter |
| 91 | `cron` | Automate tasks |
| 92 | `alias` | Create shortcuts for commands |
| 93 | `source` | Execute commands from a file in the current shell |

---

## Development and Debugging

| # | Command | Description |
|---|---------|-------------|
| 94 | `gcc` | Compile C programs |
| 95 | `make` | Build and manage projects |
| 96 | `strace` | Trace system calls and signals |
| 97 | `gdb` | Debug programs |
| 98 | `git` | Version control system |
| 99 | `vim/nano` | Text editors for scripting and editing |

---

## Other Useful Commands

| # | Command | Description |
|---|---------|-------------|
| 100 | `uptime` | Display system uptime |
| 101 | `date` | Display or set the system date and time |
| 102 | `cal` | Display a calendar |
| 103 | `man` | Display the manual for a command |
| 104 | `history` | Show previously executed commands |
| 105 | `alias` | Create custom shortcuts for commands |

---

## Basic Git Commands

> Git is your code time machine. It tracks every change, enables team collaboration without conflicts, and lets you undo mistakes. These commands help manage source code versions like a professional developer.

### Getting Started

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 1 | `git init` | Initializes a new Git repository | `git init` |
| 2 | `git clone` | Copies a remote repository to the local machine | `git clone https://github.com/user/repo.git` |
| 3 | `git status` | Displays the state of the working directory and staging area | `git status` |
| 4 | `git add` | Adds changes to the staging area | `git add file.txt` |
| 5 | `git commit` | Records changes to the repository | `git commit -m "Initial commit"` |
| 6 | `git config` | Configures user settings, such as name and email | `git config --global user.name "Your Name"` |
| 7 | `git log` | Shows the commit history | `git log` |
| 8 | `git show` | Displays detailed information about a specific commit | `git show <commit-hash>` |
| 9 | `git diff` | Shows changes between commits, working directory, and staging area | `git diff` |
| 10 | `git reset` | Unstages changes or resets commits | `git reset HEAD file.txt` |

### Branching and Merging

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 11 | `git branch` | Lists branches or creates a new branch | `git branch feature-branch` |
| 12 | `git checkout` | Switches between branches or restores files | `git checkout feature-branch` |
| 13 | `git switch` | Switches branches (modern alternative to git checkout) | `git switch feature-branch` |
| 14 | `git merge` | Combines changes from one branch into another | `git merge feature-branch` |
| 15 | `git rebase` | Moves or combines commits from one branch onto another | `git rebase main` |
| 16 | `git cherry-pick` | Applies specific commits from one branch to another | `git cherry-pick <commit-hash>` |

### Remote Repositories

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 17 | `git remote` | Manages remote repository connections | `git remote add origin https://github.com/user/repo.git` |
| 18 | `git push` | Sends changes to a remote repository | `git push origin main` |
| 19 | `git pull` | Fetches and merges changes from a remote repository | `git pull origin main` |
| 20 | `git fetch` | Downloads changes from a remote repository without merging | `git fetch origin` |
| 21 | `git remote -v` | Lists the URLs of remote repositories | `git remote -v` |

### Stashing and Cleaning

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 22 | `git stash` | Temporarily saves changes not yet committed | `git stash` |
| 23 | `git stash pop` | Applies stashed changes and removes them from the stash list | `git stash pop` |
| 24 | `git stash list` | Lists all stashes | `git stash list` |
| 25 | `git clean` | Removes untracked files from the working directory | `git clean -f` |

### Tagging

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 26 | `git tag` | Creates a tag for a specific commit | `git tag -a v1.0 -m "Version 1.0"` |
| 27 | `git tag -d` | Deletes a tag | `git tag -d v1.0` |
| 28 | `git push --tags` | Pushes tags to a remote repository | `git push origin --tags` |

### Advanced Git Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 29 | `git bisect` | Finds the commit that introduced a bug | `git bisect start` |
| 30 | `git blame` | Shows which commit and author modified each line of a file | `git blame file.txt` |
| 31 | `git reflog` | Shows a log of changes to the tip of branches | `git reflog` |
| 32 | `git submodule` | Manages external repositories as submodules | `git submodule add https://github.com/user/repo.git` |
| 33 | `git archive` | Creates an archive of the repository files | `git archive --format=zip HEAD > archive.zip` |
| 34 | `git gc` | Cleans up unnecessary files and optimizes the repository | `git gc` |

### GitHub CLI Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 35 | `gh auth login` | Logs into GitHub via the command line | `gh auth login` |
| 36 | `gh repo clone` | Clones a GitHub repository | `gh repo clone user/repo` |
| 37 | `gh issue list` | Lists issues in a GitHub repository | `gh issue list` |
| 38 | `gh pr create` | Creates a pull request on GitHub | `gh pr create --title "New Feature" --body "Description"` |
| 39 | `gh repo create` | Creates a new GitHub repository | `gh repo create my-repo` |

---

## Basic Docker Commands

> Docker packages applications into portable containers - like shipping containers for software. These commands help build, ship, and run applications consistently across any environment.

### Getting Started

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 1 | `docker --version` | Displays the installed Docker version | `docker --version` |
| 2 | `docker info` | Shows system-wide information about Docker | `docker info` |
| 3 | `docker pull` | Downloads an image from a Docker registry | `docker pull ubuntu:latest` |
| 4 | `docker images` | Lists all downloaded images | `docker images` |
| 5 | `docker run` | Creates and starts a new container from an image | `docker run -it ubuntu bash` |
| 6 | `docker ps` | Lists running containers | `docker ps` |
| 7 | `docker ps -a` | Lists all containers, including stopped ones | `docker ps -a` |
| 8 | `docker stop` | Stops a running container | `docker stop container_name` |
| 9 | `docker start` | Starts a stopped container | `docker start container_name` |
| 10 | `docker rm` | Removes a container | `docker rm container_name` |
| 11 | `docker rmi` | Removes an image | `docker rmi image_name` |
| 12 | `docker exec` | Runs a command inside a running container | `docker exec -it container_name bash` |

### Intermediate Docker Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 13 | `docker build` | Builds an image from a Dockerfile | `docker build -t my_image .` |
| 14 | `docker commit` | Creates a new image from a container's changes | `docker commit container_name my_image:tag` |
| 15 | `docker logs` | Fetches logs from a container | `docker logs container_name` |
| 16 | `docker inspect` | Returns detailed information about an object | `docker inspect container_name` |
| 17 | `docker stats` | Displays live resource usage statistics | `docker stats` |
| 18 | `docker cp` | Copies files between a container and the host | `docker cp container_name:/path /host/path` |
| 19 | `docker rename` | Renames a container | `docker rename old_name new_name` |

### Docker Networking

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 20 | `docker network ls` | Lists all Docker networks | `docker network ls` |
| 21 | `docker network create` | Creates a new Docker network | `docker network create my_network` |
| 22 | `docker network inspect` | Shows details about a Docker network | `docker network inspect my_network` |
| 23 | `docker network connect` | Connects a container to a network | `docker network connect my_network container_name` |

### Docker Volumes

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 24 | `docker volume ls` | Lists all Docker volumes | `docker volume ls` |
| 25 | `docker volume create` | Creates a new Docker volume | `docker volume create my_volume` |
| 26 | `docker volume inspect` | Provides details about a volume | `docker volume inspect my_volume` |
| 27 | `docker volume rm` | Removes a Docker volume | `docker volume rm my_volume` |

### Advanced Docker Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 28 | `docker-compose up` | Starts services defined in a docker-compose.yml file | `docker-compose up` |
| 29 | `docker-compose down` | Stops and removes services | `docker-compose down` |
| 30 | `docker-compose logs` | Displays logs for services managed by Docker Compose | `docker-compose logs` |
| 31 | `docker-compose exec` | Runs a command in a service's container | `docker-compose exec service_name bash` |
| 32 | `docker save` | Exports an image to a tar file | `docker save -o my_image.tar my_image:tag` |
| 33 | `docker load` | Imports an image from a tar file | `docker load < my_image.tar` |
| 34 | `docker export` | Exports a container's filesystem as a tar file | `docker export container_name > container.tar` |
| 35 | `docker import` | Creates an image from an exported container | `docker import container.tar my_new_image` |
| 36 | `docker system df` | Displays disk usage by Docker objects | `docker system df` |
| 37 | `docker system prune` | Cleans up unused Docker resources | `docker system prune` |
| 38 | `docker tag` | Assigns a new tag to an image | `docker tag old_image_name new_image_name` |
| 39 | `docker push` | Uploads an image to a Docker registry | `docker push my_image:tag` |
| 40 | `docker login` | Logs into a Docker registry | `docker login` |
| 41 | `docker logout` | Logs out of a Docker registry | `docker logout` |

### Docker Swarm

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 42 | `docker swarm init` | Initializes a Docker Swarm mode cluster | `docker swarm init` |
| 43 | `docker service create` | Creates a new service in Swarm mode | `docker service create --name my_service nginx` |
| 44 | `docker stack deploy` | Deploys a stack using a Compose file in Swarm mode | `docker stack deploy -c docker-compose.yml my_stack` |
| 45 | `docker stack rm` | Removes a stack in Swarm mode | `docker stack rm my_stack` |

### Docker Checkpoints

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 46 | `docker checkpoint create` | Creates a checkpoint for a container | `docker checkpoint create container_name checkpoint_name` |
| 47 | `docker checkpoint ls` | Lists checkpoints for a container | `docker checkpoint ls container_name` |
| 48 | `docker checkpoint rm` | Removes a checkpoint | `docker checkpoint rm container_name checkpoint_name` |

---

## Basic Kubernetes Commands

> Kubernetes is the conductor of your container orchestra. It automates deployment, scaling, and management of containerized applications across server clusters.

### Getting Started

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 1 | `kubectl version` | Displays the Kubernetes client and server version | `kubectl version --short` |
| 2 | `kubectl cluster-info` | Shows information about the Kubernetes cluster | `kubectl cluster-info` |
| 3 | `kubectl get nodes` | Lists all nodes in the cluster | `kubectl get nodes` |
| 4 | `kubectl get pods` | Lists all pods in the default namespace | `kubectl get pods` |
| 5 | `kubectl get services` | Lists all services in the default namespace | `kubectl get services` |
| 6 | `kubectl get namespaces` | Lists all namespaces in the cluster | `kubectl get namespaces` |
| 7 | `kubectl describe pod` | Shows detailed information about a specific pod | `kubectl describe pod pod-name` |
| 8 | `kubectl logs` | Displays logs for a specific pod | `kubectl logs pod-name` |
| 9 | `kubectl create namespace` | Creates a new namespace | `kubectl create namespace my-namespace` |
| 10 | `kubectl delete pod` | Deletes a specific pod | `kubectl delete pod pod-name` |

### Intermediate Kubernetes Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 11 | `kubectl apply` | Applies changes defined in a YAML file | `kubectl apply -f deployment.yaml` |
| 12 | `kubectl delete` | Deletes resources defined in a YAML file | `kubectl delete -f deployment.yaml` |
| 13 | `kubectl scale` | Scales a deployment to the desired number of replicas | `kubectl scale deployment my-deployment --replicas=3` |
| 14 | `kubectl expose` | Exposes a pod or deployment as a service | `kubectl expose deployment my-deployment --type=LoadBalancer --port=80` |
| 15 | `kubectl exec` | Executes a command in a running pod | `kubectl exec -it pod-name -- /bin/bash` |
| 16 | `kubectl port-forward` | Forwards a local port to a port in a pod | `kubectl port-forward pod-name 8080:80` |
| 17 | `kubectl get configmaps` | Lists all ConfigMaps in the namespace | `kubectl get configmaps` |
| 18 | `kubectl get secrets` | Lists all Secrets in the namespace | `kubectl get secrets` |
| 19 | `kubectl edit` | Edits a resource definition directly in the editor | `kubectl edit deployment my-deployment` |
| 20 | `kubectl rollout status` | Displays the status of a deployment rollout | `kubectl rollout status deployment/my-deployment` |

### Advanced Kubernetes Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 21 | `kubectl rollout undo` | Rolls back a deployment to a previous revision | `kubectl rollout undo deployment/my-deployment` |
| 22 | `kubectl top nodes` | Shows resource usage for nodes | `kubectl top nodes` |
| 23 | `kubectl top pods` | Displays resource usage for pods | `kubectl top pods` |
| 24 | `kubectl cordon` | Marks a node as unschedulable | `kubectl cordon node-name` |
| 25 | `kubectl uncordon` | Marks a node as schedulable | `kubectl uncordon node-name` |
| 26 | `kubectl drain` | Safely evicts all pods from a node | `kubectl drain node-name --ignore-daemonsets` |
| 27 | `kubectl taint` | Adds a taint to a node to control pod placement | `kubectl taint nodes node-name key=value:NoSchedule` |
| 28 | `kubectl get events` | Lists all events in the cluster | `kubectl get events` |
| 29 | `kubectl apply -k` | Applies resources from a kustomization directory | `kubectl apply -k ./kustomization-dir/` |
| 30 | `kubectl config view` | Displays the kubeconfig file | `kubectl config view` |
| 31 | `kubectl config use-context` | Switches the active context in kubeconfig | `kubectl config use-context my-cluster` |
| 32 | `kubectl debug` | Creates a debugging session for a pod | `kubectl debug pod-name` |
| 33 | `kubectl delete namespace` | Deletes a namespace and its resources | `kubectl delete namespace my-namespace` |
| 34 | `kubectl patch` | Updates a resource using a patch | `kubectl patch deployment my-deployment -p '{"spec": {"replicas": 2}}'` |
| 35 | `kubectl rollout history` | Shows the rollout history of a deployment | `kubectl rollout history deployment my-deployment` |
| 36 | `kubectl autoscale` | Automatically scales a deployment based on resource usage | `kubectl autoscale deployment my-deployment --cpu-percent=50 --min=1 --max=10` |
| 37 | `kubectl label` | Adds or modifies a label on a resource | `kubectl label pod pod-name environment=production` |
| 38 | `kubectl annotate` | Adds or modifies an annotation on a resource | `kubectl annotate pod pod-name description="My app pod"` |
| 39 | `kubectl delete pv` | Deletes a PersistentVolume (PV) | `kubectl delete pv my-pv` |
| 40 | `kubectl get ingress` | Lists all Ingress resources in the namespace | `kubectl get ingress` |
| 41 | `kubectl create configmap` | Creates a ConfigMap from a file or literal values | `kubectl create configmap my-config --from-literal=key1=value1` |
| 42 | `kubectl create secret` | Creates a Secret from a file or literal values | `kubectl create secret generic my-secret --from-literal=password=myPassword` |
| 43 | `kubectl api-resources` | Lists all available API resources in the cluster | `kubectl api-resources` |
| 44 | `kubectl api-versions` | Lists all API versions supported by the cluster | `kubectl api-versions` |
| 45 | `kubectl get crds` | Lists all CustomResourceDefinitions (CRDs) | `kubectl get crds` |

---

## Basic Helm Commands

> Helm is the app store for Kubernetes. It simplifies installing and managing complex applications using pre-packaged "charts" - think of it like apt-get for Kubernetes.

### Getting Started

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 1 | `helm help` | Displays help for the Helm CLI or a specific command | `helm help` |
| 2 | `helm version` | Shows the Helm client and server version | `helm version` |
| 3 | `helm repo add` | Adds a new chart repository | `helm repo add stable https://charts.helm.sh/stable` |
| 4 | `helm repo update` | Updates all Helm chart repositories to the latest version | `helm repo update` |
| 5 | `helm repo list` | Lists all the repositories added to Helm | `helm repo list` |
| 6 | `helm search hub` | Searches for charts on Helm Hub | `helm search hub nginx` |
| 7 | `helm search repo` | Searches for charts in the repositories | `helm search repo stable/nginx` |
| 8 | `helm show chart` | Displays information about a chart | `helm show chart stable/nginx` |

### Installing and Upgrading Charts

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 9 | `helm install` | Installs a chart into a Kubernetes cluster | `helm install my-release stable/nginx` |
| 10 | `helm upgrade` | Upgrades an existing release with a new version | `helm upgrade my-release stable/nginx` |
| 11 | `helm upgrade --install` | Installs a chart if not installed or upgrades if it exists | `helm upgrade --install my-release stable/nginx` |
| 12 | `helm uninstall` | Uninstalls a release | `helm uninstall my-release` |
| 13 | `helm list` | Lists all the releases installed on the cluster | `helm list` |
| 14 | `helm status` | Displays the status of a release | `helm status my-release` |

### Working with Helm Charts

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 15 | `helm create` | Creates a new Helm chart in a specified directory | `helm create my-chart` |
| 16 | `helm lint` | Lints a chart to check for common errors | `helm lint ./my-chart` |
| 17 | `helm package` | Packages a chart into a .tgz file | `helm package ./my-chart` |
| 18 | `helm template` | Renders the Kubernetes YAML files from a chart | `helm template my-release ./my-chart` |
| 19 | `helm dependency update` | Updates the dependencies in the Chart.yaml file | `helm dependency update ./my-chart` |

### Advanced Helm Commands

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 20 | `helm rollback` | Rolls back a release to a previous version | `helm rollback my-release 1` |
| 21 | `helm history` | Displays the history of a release | `helm history my-release` |
| 22 | `helm get all` | Gets all information for a release | `helm get all my-release` |
| 23 | `helm get values` | Displays the values used in a release | `helm get values my-release` |
| 24 | `helm test` | Runs tests defined in a chart | `helm test my-release` |

### Helm Chart Repositories

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 25 | `helm repo remove` | Removes a chart repository | `helm repo remove stable` |
| 26 | `helm repo update` | Updates the local cache of chart repositories | `helm repo update` |
| 27 | `helm repo index` | Creates or updates the index file for a chart repository | `helm repo index ./charts` |

### Helm Values and Customization

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 28 | `helm install --values` | Installs a chart with custom values | `helm install my-release stable/nginx --values values.yaml` |
| 29 | `helm upgrade --values` | Upgrades a release with custom values | `helm upgrade my-release stable/nginx --values values.yaml` |
| 30 | `helm install --set` | Installs a chart with a custom value set directly | `helm install my-release stable/nginx --set replicaCount=3` |
| 31 | `helm upgrade --set` | Upgrades a release with a custom value set | `helm upgrade my-release stable/nginx --set replicaCount=5` |
| 32 | `helm uninstall --purge` | Removes a release and deletes associated resources | `helm uninstall my-release --purge` |

### Helm Template and Debugging

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 33 | `helm template --debug` | Renders Kubernetes manifests and includes debug output | `helm template my-release ./my-chart --debug` |
| 34 | `helm install --dry-run` | Simulates the installation process | `helm install my-release stable/nginx --dry-run` |
| 35 | `helm upgrade --dry-run` | Simulates an upgrade process without applying it | `helm upgrade my-release stable/nginx --dry-run` |

### Helm and Kubernetes Integration

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 36 | `helm list --namespace` | Lists releases in a specific Kubernetes namespace | `helm list --namespace kube-system` |
| 37 | `helm uninstall --namespace` | Uninstalls a release from a specific namespace | `helm uninstall my-release --namespace kube-system` |
| 38 | `helm install --namespace` | Installs a chart into a specific namespace | `helm install my-release stable/nginx --namespace mynamespace` |
| 39 | `helm upgrade --namespace` | Upgrades a release in a specific namespace | `helm upgrade my-release stable/nginx --namespace mynamespace` |

### Helm Chart Development

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 40 | `helm package --sign` | Packages a chart and signs it using a GPG key | `helm package ./my-chart --sign --key my-key-id` |
| 41 | `helm create --starter` | Creates a new Helm chart based on a starter template | `helm create --starter https://github.com/helm/charts.git` |
| 42 | `helm push` | Pushes a chart to a Helm chart repository | `helm push ./my-chart my-repo` |

### Helm with Kubernetes CLI

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 43 | `helm list -n` | Lists releases in a specific Kubernetes namespace | `helm list -n kube-system` |
| 44 | `helm install --kube-context` | Installs a chart to a specific kubeconfig context | `helm install my-release stable/nginx --kube-context my-cluster` |
| 45 | `helm upgrade --kube-context` | Upgrades a release in a specific Kubernetes context | `helm upgrade my-release stable/nginx --kube-context my-cluster` |

### Helm Chart Dependencies

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 46 | `helm dependency build` | Builds dependencies for a Helm chart | `helm dependency build ./my-chart` |
| 47 | `helm dependency list` | Lists all dependencies for a chart | `helm dependency list ./my-chart` |

### Helm History and Rollbacks

| # | Command | Description | Example |
|---|---------|-------------|---------|
| 48 | `helm rollback --recreate-pods` | Rolls back to a previous version and recreates pods | `helm rollback my-release 2 --recreate-pods` |
| 49 | `helm history --max` | Limits the number of versions shown in release history | `helm history my-release --max 5` |

---

## Basic Terraform Commands

> Terraform lets you build cloud infrastructure with code. Instead of clicking buttons in AWS/GCP/Azure consoles, you define servers and services in configuration files.

| # | Command | Description |
|---|---------|-------------|
| 50 | `terraform --help` | Displays general help for Terraform CLI commands |
| 51 | `terraform init` | Initializes the working directory containing Terraform configuration files. Downloads necessary provider plugins |
| 52 | `terraform validate` | Validates the Terraform configuration files for syntax errors or issues |
| 53 | `terraform plan` | Creates an execution plan, showing what actions Terraform will perform |
| 54 | `terraform apply` | Applies the changes required to reach the desired state of the configuration |
| 55 | `terraform show` | Displays the Terraform state or a plan in a human-readable format |
| 56 | `terraform output` | Displays the output values defined in the Terraform configuration after an apply |
| 57 | `terraform destroy` | Destroys the infrastructure defined in the Terraform configuration |
| 58 | `terraform refresh` | Updates the state file with the real infrastructure's current state without applying changes |
| 59 | `terraform taint` | Marks a resource for recreation on the next apply |
| 60 | `terraform untaint` | Removes the "tainted" status from a resource |
| 61 | `terraform state` | Manages Terraform state files, such as moving resources between modules |
| 62 | `terraform import` | Imports existing infrastructure into Terraform management |
| 63 | `terraform graph` | Generates a graphical representation of Terraform's resources and their relationships |
| 64 | `terraform providers` | Lists the providers available for the current Terraform configuration |
| 65 | `terraform state list` | Lists all resources tracked in the Terraform state file |
| 66 | `terraform backend` | Configures the backend for storing Terraform state remotely (e.g., in S3, Azure Blob Storage) |
| 67 | `terraform state mv` | Moves an item in the state from one location to another |
| 68 | `terraform state rm` | Removes an item from the Terraform state file |
| 69 | `terraform workspace` | Manages Terraform workspaces for creating separate environments |
| 70 | `terraform workspace new` | Creates a new workspace |
| 71 | `terraform module` | Manages and updates Terraform modules (reusable configurations) |
| 72 | `terraform init -get-plugins=true` | Ensures that required plugins are fetched and available for modules |

### Terraform Environment Variables

| # | Variable | Description |
|---|----------|-------------|
| 73 | `TF_LOG` | Sets the logging level for Terraform debug output (TRACE, DEBUG, INFO, WARN, ERROR) |
| 74 | `TF_LOG_PATH` | Directs Terraform logs to a specified file |

### Terraform Cloud Commands

| # | Command | Description |
|---|---------|-------------|
| 75 | `terraform login` | Logs into Terraform Cloud or Terraform Enterprise for managing remote backends and workspaces |
| 76 | `terraform remote` | Manages remote backends and remote state storage for Terraform configurations |
| 77 | `terraform push` | Pushes Terraform modules to a remote module registry |

---

*This cheat sheet provides a comprehensive reference for DevOps professionals working with Linux, Git, Docker, Kubernetes, Helm, and Terraform.*
