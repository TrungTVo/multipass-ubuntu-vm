## Create Ubuntu multipass instance

Create new instance

```
multipass launch --name manager1
```

List all instances, along with their states and IP address

```
multipass list
```

SSH into Ubuntu multipass instance

From host machine, create SSH key pair

```
ssh-keygen -t rsa -f multipass/manager1
```

This will create `manager1` as private key and `manager1.pub` as public key under `~/.ssh/multipass/`

Copy the public key of `manager1.pub` and paste it inside the Ubuntu VM instance under `~/.ssh/authorized_keys` file. Then include this IP of the VM instance as the entry in `known_hosts` file of the host machine.

In `~/.ssh/` of the host, run (replace with IP of the instance):

```
ssh-keyscan 192.168.65.3 >> ./known_hosts
```

Then SSH into the instance with the private key:

```
ssh -i multipass/manager1 ubuntu@192.168.65.3
```
