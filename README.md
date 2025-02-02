# Ansible role `tftp`

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

An Ansible role for installing a TFTP (Trivial File Transfer Protocol) server on RHEL/CentOS 7. Specifically, the responsibilities of this role are to:

- install the necessary packages
- manage the configuration
- manage SELinux settings

For more relevant documentation on TFTP, see:

- [`tftpd(8)` man page](http://linuxmanpages.net/manpages/fedora21/man8/tftpd.8.html)
- [`tftp_selinux(8)` man page](http://linuxmanpages.net/manpages/fedora21/man8/tftpd_selinux.8.html)

## Requirements

none.

## Role Variables

The following variables can be set by the administrator:


| Variable                      | Default                              | Comments (type)                                                |
| :---                          | :---                                 | :---                                                           |
| `tftp_anon_write`             | false                                | Boolean that specifies whether SELinux allows modifying files. |
| `tftp_config`                 | /usr/lib/systemd/system/tftp.service | Path to the systemd unit file for tftp                         |
| `tftp_group`                  | root                                 | Group of the `tftp_root_directory`                             |
| `tftp_home_dir`               | false                                | Boolean that specifies whether SELinux                         |
| `tftp_mode`                   | 0755                                 | Permissions of the `tftp_root_directory`                       |
| `tftp_root_directory`         | /var/lib/tftpboot                    | The path to the root directory served by tftp.                 |
| `tftp_server_args`            | --secure                             | Command line arguments to be passed to the server executable   |
| `tftp_server_foreman_support` | false                                | Enable Foreman support by creating suitable tftpd.map          |
| `tftp_setype`                 | tftpdir_rw_t                         | SELinux context for the tftp root directory                    |
| `tftp_user`                   | root                                 | Owner of the `tftp_root_directory`                             |

## Dependencies

No dependencies.

## Testing

I use [git-worktree(1)](https://git-scm.com/docs/git-worktree) to include the test code into the working directory. Instructions for running the tests:

1. Fetch the tests branch: `git fetch origin tests`
2. Create a Git worktree for the test code: `git worktree add tests tests` (remark: this requires at least Git v2.5.0). This will create a directory `tests/`.
3. `cd tests/`
4. `vagrant up` will then create a VM and apply the second of the two available testing playbooks enumerated below.

The test playbooks:

The playbook also puts a file named README into the TFTP root directory. After applying this playbook, you should be able to fetch that file from your host system (assuming the `tftp` client is installed):

    ```ShellSession
    $ tftp 127.0.0.1 6969 -c get README
    ```

The TFTP port (69) on the VM is forwarded through the NAT interface to port 6969 on your host system, hence the 127.0.0.1 and port number in the command line.

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section. Pull requests are also very welcome. Preferably, create a topic branch and when submitting, squash your commits into one (with a descriptive message).

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟
