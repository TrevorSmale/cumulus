+++
title = "WSL2"
description = "Windows Subsystem for Linux 2"
weight = 2
+++

##  Windows Subsytem for Linux overview

{{< lead >}}
Ubuntu WSL2, or Windows Subsystem for Linux 2, is a compatibility layer that allows running Ubuntu, a popular Linux distribution, on Windows 10 or Windows Server. It provides a seamless integration of Ubuntu within the Windows operating system, enabling users to execute Linux commands and run Linux applications without the need for virtual machines. WSL2 offers improved performance compared to its predecessor, WSL1, by utilizing a full Linux kernel running in a lightweight virtual machine. With Ubuntu WSL2, developers and users can leverage the power of Linux tools and utilities while still benefiting from the familiarity and convenience of the Windows environment.
{{< /lead >}}

## Issues I have experienced

{{< panel title="VSCODE CLI Problem" style="danger" >}}
I normally invoke VSCODE within Ubuntu WSL2 CLI with:
    $ code Documents/Git/Project
Which opens VSCODE to that target directory.
However I started getting an error regarding the path to VSCODE being broken
{{< /panel >}}

{{< panel title="VSCODE CLI Solution" style="success" >}}
* Within the WSL terminal, type rm -r ~/.vscode-server to delete the VS Code WSL server.
* Exit the terminal and from your PowerShell/Cmd, run wsl --shutdown.
{{< /panel >}}

---

{{< panel title="GO Path Variable constant reset" style="danger" >}}
Go Path variable keeps resetting in WSL2:
{{< /panel >}}

{{< panel title="GO Path Variable solution" style="success" >}}
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
{{< /panel >}}