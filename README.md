# Example Ansible project: DigitalOcean + Nginx/Let’s Encrypt

This is a reference/template project to quickly launch a new droplet on DigitalOcean and set up Nginx with Let’s Encrypt-controlled SSL certificate.


## Requirements

You must have Ansible installed locally (tested with Ansible 2.9.10 on macOS).

Use the following to install it on macOS under Brew:

~~~sh
brew install ansible
~~~

## Preparing DigitalOcean

At DigitalOcean, you must receive the OAuth API key.

Visit the DigitalOcean control panel; find the “API” menu item; visit the “Tokens/Keys” item; and press “Generate New Token”.

You will make a token (name it as you wish; you need to enable “Write” option, though it is enabled by default). This token will be used in future operations to access the DO API.  This token is a long line (likely, 64 symbols long). You will use it later during the playbook launch.

## How to launch

In the `ansible/inventories`, you should create an inventory file with the server(s) you want to deploy Nginx and Let’s Encrypt to.
In the example below, we use the `production.yml` file, which sets up two .

Instead of `$YOUR_DO_API_KEY`, you must put your real API key.

~~~sh
DO_API_KEY=$YOUR_DO_API_KEY ansible-playbook --inventory=ansible/inventories/production.yml ansible/site.yml
~~~

Look at this inventory file; it describes two hosts under construction, `a1` and `a2`. These name should be unique in your Digital Ocean account; and these hosts will be created (unless already exist); or, if they are present already – their IPs will be discovered.

---

(C) 2020 Alex Myodov
