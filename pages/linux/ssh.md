# shh

> OpenSSH SSH Client

- remotely log in to a server

`ssh {{user}}@{{server_address}}`

- use a jump box as a proxy to log in to a server (not accessible from a public subnet)

`ssh -t {{user}}@{{jump_box_address}} ssh {{user}}@{{server_address}}`

- copy your ssh public key to a server for password-less login

`cat ~/.ssh/id_rsa.pub | ssh {{user}}@{{server_address}} "mkdir ~/.ssh; cat >> ~/.ssh/authorized_keys"`

- execute single command over ssh

`ssh {{user}}@{{server_address}} ifconfig`

- execute commands over ssh that require pseudo-terminal allocation

`ssh {{user}}@{{server_address}} -t tmux`

- execute list of cmds in a cmd.txt file over ssh

```ssh {{user}}@{{jump_box_address}} {{user}} "`cat cmd.txt`"```

- tunnel traffic from your local on port 3000 to the remote server on port 80 (keep in foreground)

`ssh -N -L3000:localhost:80 {{user}}@{{server_address}}`

- tunnel traffic from your local on port 3000 to the remote server on port 80 (force to background)

`ssh -f -N -L3000:localhost:80 {{user}}@{{server_address}}`
