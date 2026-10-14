
And that wraps it up! You’ve managed to set up a server without writing any `apt` commands and now we have just completed a zero downtime setup that makes your life pretty easy. No need of logging in to the servers to do manual `git` fetches and migrations. Truth be told, we are humans and we tend to forget. Ever had a bug that takes you a day to debug only to realise you did not restart a given service? Well, with this automation, you only setup once and the rest is taken care of.

## And There’s More!

It doesn’t stop there - PHP is just one of the languages you can use with this type of pipeline! The automation world is so huge you can automate anything that makes you feel like you’re wasting time. This is just the tip of the iceberg, go out and do wonders!

# Document Outline

*   [Contents](#index_split_000.html#p2)
*   [Preface](#index_split_000.html#p4)
    *   [How this book is designed](#index_split_000.html#p5)
    *   [Who should read this book?](#index_split_000.html#p6)
    *   [Notice of Liability](#index_split_000.html#p7)
*   [Manual Server Setup](#index_split_000.html#p8)
    *   [Finding the Right Server](#index_split_000.html#p9)
    *   [Server Updates](#index_split_000.html#p11)
    *   [Unattended Upgrades](#index_split_000.html#p12)
    *   [Installing Build Tools](#index_split_000.html#p14)
    *   [Setting Up MySQL Server](#index_split_000.html#p15)
    *   [Setting Up PHP 7.4](#index_split_000.html#p17)
    *   [Setting Up Redis Server](#index_split_000.html#p19)
    *   [Setting Up Nginx](#index_split_000.html#p20)
*   [Automated Server Setup using Ansible](#index_split_000.html#p24)
    *   [What is Ansible?](#index_split_000.html#p25)
    *   [Setting up Ansible](#index_split_000.html#p26)
    *   [Ansible Inventory](#index_split_000.html#p28)
    *   [YAML Basics](#index_split_000.html#p30)
    *   [Ansible Playbooks](#index_split_000.html#p32)
    *   [Role Structure](#index_split_000.html#p36)
    *   [The Common Role](#index_split_000.html#p37)
    *   [The MySQL Role](#index_split_000.html#p54)
    *   [The PHP Role](#index_split_000.html#p61)
    *   [The Nginx Role](#index_split_000.html#p71)
    *   [The ACL Role](#index_split_000.html#p86)
*   [Testing & Deployment](#index_split_000.html#p88)
    *   [Test Cases](#index_split_000.html#p89)
    *   [Local Testing](#index_split_000.html#p90)
    *   [Automated Testing with GitLab CI/CD](#index_split_000.html#p109)
    *   [Automated Deployment with GitLab CI/CD](#index_split_000.html#p119)
    *   [Laravel Envoy](#index_split_000.html#p121)
    *   [Deployment](#index_split_000.html#p127)
    *   [And There’s More!](#index_split_000.html#p131)
