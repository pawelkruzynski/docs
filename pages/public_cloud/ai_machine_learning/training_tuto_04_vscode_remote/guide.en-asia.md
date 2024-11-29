---
title: AI Training - Tutorial -  Connect to VSCode via remote
excerpt: Tutorial to configure Remote Visual Studio with AI Training
updated: 2022-09-01
---

## Objective

This tutorial covers the process of starting a job using a Visual Studio Code Remote via SSH.

## Requirements

-   an **AI Training project** created inside a **Public Cloud** project
-   a [user for AI Training](/pages/public_cloud/ai_machine_learning/gi_01_manage_users)
-   installing the [OVHcloud AI CLI](/pages/public_cloud/ai_machine_learning/cli_10_howto_install_cli)

> [!warning]
> The deployed image needs to contain the `bash` binary and a glibc-based Linux (Ubuntu / Debian)

## Installation

1.  Install an [OpenSSH compatible SSH client](https://code.visualstudio.com/docs/remote/troubleshooting#_installing-a-supported-ssh-client) if one is not already present.
2.  Install [Visual Studio Code](https://code.visualstudio.com/).
3.  Install the [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).

## Start a job with the SSH feature

We will launch a job with the CLI, just choose the number of GPUs (`<nb-gpus>`) to use on your job and use the following command:

``` {.bash}
ovhai job run --gpu <nb-gpus> -s ~/.ssh/id_ed25519.pub ovhcom/ai-training-tensorflow:2.3.0
```

Once the job is `Running`, you can see the `sshUrl` with *job get*:

``` {.bash}
ovhai job get <job-id>
```

## Configure VSCode Remote Development

Verify you can connect to the SSH host by running the following command from a terminal / PowerShell window replacing user\@hostname accordingly:

``` {.bash}
ssh <job-id>@gra.ai.cloud.ovh.net

Welcome to OVHcloud AI Training Jobs SSH
job-0d916855-1cd4-4b66-8803-b4782bc13902:~$
```

Click on the Remote Explorer Button.

![image](images/vscode-1.png){.thumbnail}

Then click on the `+` button to add a SSH server.

![image](images/vscode-2.png){.thumbnail}

Then click on the window icon near your server in the list.

![image](images/vscode-3.png){.thumbnail}

Enjoy.

![image](images/vscode-4.png){.thumbnail}

## Go further

- Check how to run Tensorflow code with GPUs [here](/pages/public_cloud/ai_machine_learning/training_tuto_03_tensorflow_gpu).
- You can compare AI models based on resource consumption, accuracy and training time. Refer to this [tutorial](/pages/public_cloud/ai_machine_learning/training_tuto_06_models_comparaison_weights_and_biases).

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/asia/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.gg/ovhcloud)
