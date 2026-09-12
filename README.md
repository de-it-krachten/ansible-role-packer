[![CI](https://github.com/de-it-krachten/ansible-role-packer/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-packer/actions?query=workflow%3ACI)


# ansible-role-packer

Install hashicorp packer



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Ubuntu 26.04 LTS
- Fedora 43
- Fedora 44<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms


## Role Variables
### defaults/main.yml
<pre><code>
# Packer OS packages
packer_packages:
  - packer

# product platform
packer_platform: "{{ ansible_facts.system | lower }}"

# product architecture
packer_arch: "{{ 'amd64' if ansible_facts.architecture == 'x86_64' else ansible_facts.architecture }}"

# product install mode (binary or package)
packer_install_mode: package

# product zip filename
packer_zip: >-
  packer_{{ packer_version }}_{{ packer_platform }}_{{ packer_arch }}.zip

# product download url
packer_product_url: >-
  https://releases.hashicorp.com/packer/{{ packer_version }}/{{ packer_zip }}

# List of packer plugin to install
packer_plugins: []

# User to install plugins for
packer_plugins_user: root

# Execute packer build phase
packer_build: false

# Destroy already existing VM (clean start)
packer_vm_destroy: true

# Virtual environment with the required ansible version
# packer_ansible_venv: /usr/local/venv/ansiblecore216
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'packer'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'packer'
      ansible.builtin.include_role:
        name: packer
</pre></code>
