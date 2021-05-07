# HW1

This homework will guide you to practice with basic virtualization technology and familiarize you with building node CLI programs.

## Class activities (50)

Complete the following class activities. Document in your HW's README.md

* [ ] Discussion: Describe a situation where it was difficult to run code from someone else (4)
* [ ] Complete "On your own": Ubuntu up script (10)
* [ ] Complete the [CLI notebook](https://docable.cloud/chrisparnin/notebooks/nodejs/CLI/cli.md) (6)
* [ ] Complete "Docker workshop" (10)

Answer the following conceptual questions (20)

* Why can code be difficult to run on another machine? 
* Explain the concepts of a computing environment and headless infrastructure.
* Compare full emulation virtualization vs. binary translation
* What are some use cases associated with microvms and unikernels?
* In VM workshop, why can't the eth0 ip address be pinged from the host?
* How can bakerx access the virtual machine through ssh?
* What are the limitations of using chroot for os-virtualization?
* Why is the builder pattern useful for building images?

## Virtual Machine provisioning with CLI program (40)

You will start with a starter code base and modify it to fulfill the homework criteria.
Please do the following before you start the homework.

### Prepare your GitHub Repo.

Sign into [NCSU's GitHub](https://github.ncsu.edu/).

1. Go to the repository: `https://github.ncsu.edu/cscdevops-spring2021/HW1-<unity>`
2. **Do not create any content, yet**
 
### Clone and set-url

3. Clone the following template repository. Then, modify the git remote url so that it now will point to your HW1-<unity> repo.

```bash
git clone http://github.com/CSC-DevOps/V
cd V
git remote -v
git remote set-url origin https://github.ncsu.edu/cscdevops-spring2021/HW1-<unity>
```

### Install and test

Install the npm packages, then create a symlink for running your program.
```bash
npm install
npm link
```

Try it out.
```
v up
```

You will see a virtual machine being prepared and booted; however, **it will hang as the network and port forwarding for ssh is not ready**.

```
Executing VBoxManage import "/Users/cjparnin/.bakerx/.persist/images/bionic/box.ovf" --vsys 0 --vmname V
Executing VBoxManage modifyvm "V" --memory 1024 --cpus 1
Executing VBoxManage modifyvm V  --uart1 0x3f8 4 --uartmode1 disconnected
Running VM customizations...
Executing VBoxManage startvm V --type emergencystop
Executing VBoxManage startvm V --type headless
Waiting for ssh to be ready on localhost:2800...
```

#### VM setup (15 points)

Add the following required components to your project by editing the [`customize(name)`](https://github.com/CSC-DevOps/V/blob/14c48245080b6eb8968175bd07d48a810dc4c3ea/commands/up.js#L92-L95) function inside commands/up.js. You will want to take advantage of the `VBoxManage.execute` wrapper to execute VirtualBox commands.

* Add a NIC with NAT networking.
* Add a port forward from 2800 => 22 for guestssh.
* Add a port forward from 9000 => 5001 for a node application.

#### Post-Configuration (10 points)

Add the following required components to your project by editing the [`postconfiguration(name)`](https://github.com/CSC-DevOps/V/blob/master/commands/up.js#L100) function inside the commands/up.js. You will want to take advantage of the ssh command wrapper to send commands to the VM.

* Install nodejs, npm, git
* Clone https://github.com/CSC-DevOps/App
* Install the npm packages

**Warning** 💥: Be mindful of the deadly mix of quotes, platforms, and operators for combining (&&)---they are inconsistent on platforms and you may accidently be running the second command on your host system instead of remote system.

#### SSH and App (15 points)

Add a new command by creating a ssh.js inside the commands directory. 
When running `v ssh` it should ssh into your VM (25 points).

* Implement and demonstrate running `v ssh`.
* Manually run `node main.js start 5001`.
* Demonstrate you can visit `localhost:9000` to see your running App.

#### Extra Requirements

You can complete some or all of the following activities for extra credit by modifying your code.

* Create a second NIC with host-only networking enabled and set the IP address to 192.168.33.10. Demonstrate that you can use your IP address to visit [http://192.168.33.10:5001/](http://192.168.33.10:5001/) to see your running App. (5 points)
  > Note: to receive full credit, you must dynamically detect the host-only interface (or create it, if doesn't exist), instead of hard-coding the interface name (hint: see [here](https://www.virtualbox.org/manual/ch08.html#idp16668048)).

* Create a shared sync folder mapping the (current working directory on your host => /V inside the VM). This can be fairly involved, only attempt if experienced---limited help will be provided from teaching staff. (5 points)

## Screencast (10)

Create a screencast of your assignment:

* Demonstrate running your code to provision the VM (`v up`), running your customization and post-configuration steps, and ssh (`v ssh`) and a starting your App. Demonstrate your app running on your browser. Demonstrate any extra requirements fulfilled.

For guidelines, software, and recommendations see [Screencasts](Screencasts.md).

## Evaluation

* Class activities (50)
* VM code (40)
* Screencast (10)
* Extra requirements (+5/+5)

Max possible score: 110/100.

## Submission

Please commit your code by the deadline, including a README.md describing what you implemented, and includes a link to a screencast.

The assignment is due Friday, Feb 12th---before midnight.
