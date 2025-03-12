## Global

##### Generate an SSH Public Key
```
ssh-keygen -t rsa
```

`You will be asked to define a location to save the key pair.`
`Generating public/private rsa key pair.`
`Enter file in which to save the key (/home/vyom/.ssh/id_rsa):`
`/home/vyom/.ssh/id_rsa already exists.`
`Overwrite (y/n)? y`

##### Permissions:

700 - .ssh (Directory)
600 - Private Key
644 - Public Key (.pub)

___

## GitHub

### (001) Error: Agent admitted failure to sign

When trying to SSH into GitHub.com on a Linux computer, you may see the following message in your terminal:

```
ssh -vT git@github.com
```

```shell
> ...
> Agent admitted failure to sign using the key.
> debug1: No more authentication methods to try.
> Permission denied (publickey).
```

#### *Resolution*

You should be able to fix this error by loading your keys into your SSH agent with `ssh-add`:

```shell
# start the ssh-agent in the background
eval "$(ssh-agent -s)"
> Agent pid 59566

ssh-add
> Enter passphrase for /home/YOU/.ssh/id_rsa: [tippy tap]
> Identity added: /home/YOU/.ssh/id_rsa (/home/YOU/.ssh/id_rsa)
```

If your key does not have the default filename (`/.ssh/id_rsa`), you'll have to pass that path to `ssh-add`:

```shell
# start the ssh-agent in the background
eval "$(ssh-agent -s)"
> Agent pid 59566

ssh-add ~/.ssh/my_other_key
> Enter passphrase for /home/YOU/.ssh/my_other_key: [tappity tap tap]
> Identity added: /home/YOU/.ssh/my_other_key (/home/YOU/.ssh/my_other_key)
```

___

