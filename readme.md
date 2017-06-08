# Vagrant BuzzingPixel LEMP environment

This environment uses Ubuntu (16.0.4), NGINX, and via FPM, various versions of PHP: 5.3.29, 5.6.30, 7.0.18, and 7.1.3. This box closely resembles the custom Digital Ocean base droplet used to spin up a new BuzzingPixel server. If you ask nicely, I might even be inclined to create a snapshot of it and transfer it to you if you like.

## Requirements

You will need to have [Vagrant](https://www.vagrantup.com/) and [VirtualBox](https://www.virtualbox.org/) installed.

To use NFS on Windows (you want to use NFS, it will speed up page loads by about 800%), you will need to have the [Vagrant WinNFSd] plugin installed. Thankfully it's as simple as running `vagrant plugin install vagrant-winnfsd` from command prompt or PowerShell.

## Getting Started

To get started:

1. Add the `localStorage`, `nginxConfigs`, and `scripts` directories with contained files and directories, and the `Vagrantfile` to your project
2. Edit the example sync directories in the vagrant file to sync directories as needed for your setup
3. Edit site.conf to suite the needs of your project (and even add other site configs or change the name)
4. Duplicate `vagrantConfig.yaml.sample` and use an IP address that does not conflict with any other IP addresses for other vagrant boxes on your setup.
    - You should continue using the `192.168.56.xxx` address space since that is VirtualBox’s internal address space.
5. Then you can run `vagrant up`

## Daily Usage

`vagrant up` starts the box, `vagrant halt` stops the box as always.

The command line version of PHP after initial setup will default to 7.1.3. To switch PHP versions quickly on the fly, run `vagrant ssh`, then once SSHed into the box, use one of the commands shown to you when you log in (like `php55`) to switch which PHP version is being used. You can also quickly restart NGINX and all PHP-FPM versions by typing `restartServices`.
