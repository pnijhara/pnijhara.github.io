---
title: "Install Chocolatey on Windows"
date: 2021-05-21T11:41:05+05:30
categories:
- Hugo
- Random Discovery
tags:
- AMU-OSS
- Windows
keywords:
- tech
autothumbnailImage: false
---
In my first blog on Hugo [^footnote], I have written a command on how to install Hugo on a Windows machine.

``` shell
> choco install hugo -confirm
```
A lot of people asked me about `choco` and how to install it. So, in this blog, I will write the steps involved in installing Chocolatey.

## What is Chocolatey?

Chocolatey is a software management solution that gives you the freedom to create a simple software package and then deploy it anywhere you have Windows using any of your familiar configuration or system management tools. Chocolatey brings the concepts of true package management to allow you to version things, manage dependencies and installation order, better inventory management, and other features.

It is similar to apt, yum, brew or Pacman or indeed any other package managers for Linux or Mac. But Chocolatey is for Windows. So, giving the Windows users the same level of power.

## How to install Chocolatey?

1. Open Powershell as "Administrator" (very important, else the rest of the commands won't work)
2. Check your execution policies first with the following command
    ```shell
    > Get-ExectionPolicy
    ```
    Chances are high that you might receive `unrestricted` as output.
3. We need all the policies signed
    ```shell
    > Set-ExecutionPolicy AllSigned
    ```
4. Run the following command. But before that recheck your execution policies.
    ```shell
    > Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    ```

And it's done. See `choco` in acton:
![gif](https://docs.chocolatey.org/assets/images/gifs/choco_install.gif)

[^footnote]: Read "Create your own blog in 30 minutes using Hugo, a static site generator written in Go" &rarr; https://pnijhara.github.io/2019/08/create-your-own-blog-in-30-minutes-using-hugo-a-static-site-generator-written-in-go/
