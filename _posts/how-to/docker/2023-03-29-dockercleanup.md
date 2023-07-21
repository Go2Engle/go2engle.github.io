---
title: Clean-up docker
date: 2023-03-29
categories: [How-to, Docker]
tags: [docker,container]     # TAG names should always be lowercase
---

## Introduction

A problem I have ran into many of times on docker host when trying to prune them is the overlays2 folder still contains large amounts of data. Running the correct prune command when on the latest version of docker seems to do the trick.

## Steps
1. Updated to the latest version of docker
2. Run the below command.
    ```shell
    docker system prune -a -f
    ```