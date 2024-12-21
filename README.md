## Setting Up GitHub SSH Authentication on MacOS

In order for GitHub to deem our machines as "safe" to push code, we need to setup an identification key known as an `ssh key`.

Enter the following commands in your terminal, with your ***own*** information inserted:

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

The above email ***must*** be your GitHub email!

You should see the following prompt:

```sh
> Enter a file in which to save the key (/Users/you/.ssh/id_ed25519):
```

Leave it blank and hit <kbd>return</kbd> to save it in a default file.

You'll now be prompted to password protect the ssh key, but we can skip this portion. When prompted with the following, **hit** <kbd>return</kbd> **to leave the password as blank, both times**:

```sh
> Enter passphrase (empty for no passphrase):
> Enter same passphrase again:
```

Now, let's start the MacOS ssh-agent. Enter the following command into your terminal:

```sh
eval "$(ssh-agent -s)"
```

Now copy the ssh key to your clipboard with this command:

```sh
pbcopy < ~/.ssh/id_ed25519.pub
```

To complete this setup, follow the instructions starting from Step 2 at this link **[HERE](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)**.

To check your installation, run:

```bash
ssh -T git@github.com
```

You should see output similar to:

```
Hi <you>! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

## Setting Up GitHub SSH Authentication on Windows/Ubuntu


To create a SSH key, enter the following command in your terminal:

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**NOTE**: Be sure to replace `your_email@example.com` with the email that you have registered with GitHub.

When you're prompted to `Enter a file in which to save the key,` press <kbd>Enter</kbd>. This accepts the default file location.

When prompted for a password, hit <kbd>Enter</kbd> twice to skip this step:

```sh
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

We'll now start the SSH agent, enter the following command into your terminal:

```sh
eval "$(ssh-agent -s)"
```

Now enter the following command into your terminal:

```sh
ssh-add ~/.ssh/id_ed25519.pub
```

Now let's make your new ssh key visible in the terminal by entering the following command into your terminal:

```sh
cat ~/.ssh/id_ed25519.pub
```

Now we can copy our SSH key by selecting the output of that command and using for the next step below.

Follow the steps outlined **[HERE](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)** starting from Step 2. We've already completed Step 1.