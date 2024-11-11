---
title: "How NPM broke my server"
date: 2024-10-20
draft: false
showTitle: true
---

I own a small **1vCPU** and **1GB** RAM Digital Ocean Droplet. Which costs  me aroud  500rs per month.

So, Last week I was trying to build a Documentation website with [Docusaurus](https://docusaurus.io/) for a project. I have pushed the project to GitHub and cloned it to my server.

Then I started installing with npm. I ran `npm install` and it started installing the dependencies. After a few minutes, I got an error saying that the server is out of memory. I was surprised because I have only 1GB of RAM and the server was not doing anything else. And The CPU and Disk usage was very high.

I checked the memory usage with `htop`. But I couldn't figure it out because the server was unresponsive. I had to reboot the server to get it back online.

I tried to install the dependencies again, but the same thing happened. I was frustrated and started searching for the issue. I found that npm uses a lot of memory to install the dependencies. I tried to increase the swap memory, but it didn't help.

Then I was fed up using npm and according to few reddit posts they mentioned that `pnpm` is a good alternative to npm. So I tried to install pnpm with `npm install -g pnpm`. It worked and I tried to install the dependencies with `pnpm install`. It worked like a charm. I was able to install the dependencies without any issues.

## Reason behind the issue

- NPM installs the dependencies in a flat structure. So if a package is used in multiple dependencies, it will be installed multiple times. This will increase the size of the `node_modules` folder.

- NPM uses a lot of memory to install the dependencies. So if you have a small server, it will run out of memory.

- NPM uses a lot of disk space to install the dependencies. So if you have a small disk space, it will run out of disk space.

## Conclusion

- If you have a small server, use `pnpm` instead of `npm` to install the dependencies.

- If you have a large server, you can use `npm` to install the dependencies.

- If you have a large server and want to save disk space, you can use `yarn` to install the dependencies.

### Links
- [pnpm](https://pnpm.io/)
- [Docusaurus](https://docusaurus.io/)
- [Digital Ocean](https://www.digitalocean.com )
