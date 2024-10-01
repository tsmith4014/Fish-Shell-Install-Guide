# Installing Fish Shell on macOS

1. **Install Homebrew (if you don't have it installed already)**:
   Homebrew is a package manager for macOS that simplifies the installation of software. It installs tools and applications in a consistent and convenient way.

   Open your terminal and run:

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

   - `/bin/bash -c`: Executes the command in a new instance of the bash shell.
   - `curl -fsSL`: This command downloads the Homebrew installer script. The `-f` flag ensures the download fails on errors, `-s` makes curl operate silently, and `-L` follows redirects.

2. **Install Fish using Homebrew**:
   Once Homebrew is installed, use the following command to install Fish:

   ```bash
   brew install fish
   ```

   - `brew install fish`: Instructs Homebrew to install the Fish shell. Homebrew automatically downloads the latest stable version of Fish and installs it on your system.

3. **Set Fish as your default shell**:
   To set Fish as your default shell, you need to add its path to the list of recognized login shells (`/etc/shells`) and then change your default shell.

   First, add Fish to the list of recognized shells:

   ```bash
   echo /opt/homebrew/bin/fish | sudo tee -a /etc/shells
   ```

   - `echo /opt/homebrew/bin/fish`: Prints the path of Fish shell.
   - `sudo tee -a /etc/shells`: The `sudo` command gives you root privileges to modify `/etc/shells`, which lists available login shells. The `-a` flag appends the Fish shell path to the file.

   Then, change your default shell to Fish:

   ```bash
   chsh -s /opt/homebrew/bin/fish
   ```

   - `chsh -s /opt/homebrew/bin/fish`: This command changes your default shell to Fish (`chsh` stands for "change shell"). The `-s` flag specifies the new shell's path.

4. **Start Fish**:
   Open a new terminal or type `fish` to start the Fish shell immediately:
   ```bash
   fish
   ```

---

## Installing Fish Shell on Windows

### Using Windows Subsystem for Linux (WSL) **(Mac above should work but below has not been tested, paths may need adjustment)**

1. **Enable WSL** (if not enabled yet):
   Windows Subsystem for Linux (WSL) allows you to run Linux distributions natively on Windows without the overhead of a virtual machine.

   Open PowerShell as Administrator and run:

   ```bash
   wsl --install
   ```

   - `wsl --install`: This command installs WSL along with a default Linux distribution (Ubuntu). WSL is a compatibility layer that lets you run Linux commands on Windows.

2. **Install a Linux distribution**:
   After enabling WSL, install your preferred Linux distribution (like Ubuntu) from the Microsoft Store.

3. **Install Fish in the WSL environment**:
   Once WSL is set up and running, open your installed Linux distribution and use the following commands to install Fish:

   ```bash
   sudo apt update
   sudo apt install fish
   ```

   - `sudo apt update`: This command updates the list of available packages and their versions from the repositories. The `sudo` command is used to execute commands with superuser privileges.
   - `sudo apt install fish`: This command installs Fish by fetching it from the package repository and installing it on your system.

4. **Set Fish as your default shell** in WSL:
   After installing Fish, you can set it as your default shell by running:

   ```bash
   chsh -s /usr/bin/fish
   ```

   - `chsh -s /usr/bin/fish`: The `chsh` command changes your default login shell, and `-s /usr/bin/fish` specifies Fish as the default shell (this is where Fish is typically installed in most Linux distributions).

   The next time you open your WSL terminal, Fish will automatically start.

#### Using Cygwin on Windows (Alternative method)

1. **Download and install Cygwin**:
   Cygwin provides a large collection of GNU and Open Source tools which provide functionality similar to a Linux distribution on Windows.

   Download Cygwin from [Cygwin’s website](https://www.cygwin.com/). During installation, ensure that you select the `fish` package from the list of available packages in the Cygwin setup interface. This will install Fish along with the basic Cygwin tools.

2. **Launch Fish**:
   After installation, open the Cygwin terminal and type:
   ```bash
   fish
   ```
   This starts the Fish shell.

---

### Additional Tips for Both Platforms

- **Customizing Fish**: Once Fish is installed, you can customize it by creating or modifying the `~/.config/fish/config.fish` file. You can add aliases, change the prompt, and more.
- **Fish Plugins**: Fish has a plugin manager called Fisher that allows you to easily install and manage plugins. You can install Fisher by running:
  ```fish
  curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
  ```
  Then, you can use Fisher to add useful plugins to enhance your Fish shell experience.

---
