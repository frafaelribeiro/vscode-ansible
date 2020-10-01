# vscode-ansible incorret modules url

Correcting the URL pointing in ansible modules in vscode.

extension version: 0.5.2
OS: Linux Ubuntu

issue: module, documentation at http://docs.ansible.com/ansible/command_module.html
receive error 404: The version of the Ansible documentation you were looking at doesn’t contain that page.


workaround:

``` bash
$ cd .vscode/extensions/vscoss.vscode-ansible-0.5.2/

:~/.vscode/extensions/vscoss.vscode-ansible-0.5.2$ vim out/completionData.js

change to this
item.documentation = `http://docs.ansible.com/ansible/latest/modules/${module.module}_module.html`;

:~/.vscode/extensions/vscoss.vscode-ansible-0.5.2$ vim out/server/services/yamlHover.js

change to this
contents: `module, documentation at http://docs.ansible.com/ansible/latest/modules/${content}_module.html`,

:~/.vscode/extensions/vscoss.vscode-ansible-0.5.2$ vim server/src/services/yamlHover.ts

change to this
contents: `module, documentation at http://docs.ansible.com/ansible/latest/modules/${content}_module.html`,

```

To remote ssh or WSL, use the same workaround.
