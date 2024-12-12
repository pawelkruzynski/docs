---
title: AI Deploy - Apps portfolio
excerpt: A collection of AI apps that can be easily deployed with AI Deploy
updated: 2023-04-04
---

> [!primary]
>
> AI Deploy is covered by **[OVHcloud Public Cloud Special Conditions](https://storage.gra.cloud.ovh.net/v1/AUTH_325716a587c64897acbef9a4a4726e38/contracts/d2a208c-Conditions_particulieres_OVH_Stack-WE-9.0.pdf)**.
>

## Objective

AI Deploy allows you to deploy AI apps or models. To test or use the product, you can build on existing AI models.

For example, you can rely on **open-source** models or apps.

## Portfolio of AI apps and models

To test **AI Deploy**, you can quickly deploy apps based on those proposed in our portfolio.

### Quick examples

| Owner | Task | Description | Documentation | Dockerfile | Docker image | CLI command | Usage |       
|-------|------|-------------|---------------|------------|--------------|-------------|-------|
| OVHcloud | Hello world | Launch your first API with Flask | [AI Deploy - Getting started](/pages/public_cloud/ai_machine_learning/deploy_guide_02_getting_started) | [Dockerfile - Hello world](https://github.com/ovh/ai-training-examples/blob/main/apps/flask/hello-world/Dockerfile) | `priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/ai-deploy-hello-world` | `ovhai app run priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/ai-deploy-hello-world` | **API** - interact with the API with a curl command or a Python script |
| OVHcloud | EDA and interactive prediction | Explore, analyse iris data and do interactive prediction with Streamlit | [AI Deploy - Tutorial - Deploy an interactive app for EDA and prediction using Streamlit](/pages/public_cloud/ai_machine_learning/deploy_tuto_07_streamlit_eda_iris) | [Dockerfile - EDA and prediction on iris data](https://github.com/ovh/ai-training-examples/blob/main/apps/streamlit/eda-classification-iris/Dockerfile) | `priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/streamlit-eda` | `ovhai app run priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/streamlit-eda` | **Web interface** - access to the app with the url |
| OVHcloud | Sketch recognition | Recognize handwritten digits with Gradio | [AI Deploy - Tutorial - Deploy a Gradio app for sketch recognition](/pages/public_cloud/ai_machine_learning/deploy_tuto_05_gradio_sketch_recognition) | [Dockerfile - Sketch recognition](https://github.com/ovh/ai-training-examples/blob/main/apps/gradio/sketch-recognition/Dockerfile) | `priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/gradio-sketch-recognition` | `ovhai app run priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/gradio-sketch-recognition` | **Web interface** - access to the app with the url |
| OVHcloud | Spam classification | Classify spam messages with FastAPI | [AI Deploy - Tutorial - Deploy and call a spam classifier with FastAPI](/pages/public_cloud/ai_machine_learning/deploy_tuto_08_fastapi_spam_classifier) | [Dockerfile - Spam classifier API](https://github.com/ovh/ai-training-examples/blob/main/apps/fastapi/spam-classifier-api/Dockerfile) | `priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/fastapi-spam-classification` | `ovhai app run priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/fastapi-spam-classification` | **API** - interact with the API with `<app-url>/docs` or curl command |
| OVHcloud | Sentiment analysis | Analyse text sentiment with Hugging Face models and Flask | [AI Deploy - Tutorial - Deploy an app for sentiment analysis with Hugging Face and Flask](/pages/public_cloud/ai_machine_learning/deploy_tuto_06_flask_hugging_face) | [Dockerfile - Sentiment analysis Hugging Face app](https://github.com/ovh/ai-training-examples/blob/main/apps/flask/sentiment-analysis-hugging-face-app/Dockerfile) | `priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/flask-sentiment-analysis` | `ovhai app run priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/flask-sentiment-analysis` | **Web interface** - access to the app with the url |
| OVHcloud | Speech-to-Text | Use Speech-to-Text powers on audio and video | [AI Deploy - Tutorial - Create and deploy a Speech to Text application using Streamlit](/pages/public_cloud/ai_machine_learning/deploy_tuto_09_streamlit_speech_to_text_app) | [Dockerfile - Speech-to-Text Streamlit app](https://github.com/ovh/ai-training-examples/blob/main/apps/streamlit/speech-to-text/Dockerfile) | `priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/streamlit-speech-to-text` | `ovhai app run priv-registry.gra.ai.cloud.ovh.net/ai-deploy-portfolio/streamlit-speech-to-text` | **Web interface** - access to the app with the url |

If you want to launch these apps from the OVHcloud control panel, fill in the name of the docker image in **Step 2 - Application to deploy**.

> [!primary]
>
> Each of the following apps launches on port `8080`. You don't need to enter it in the launch command.
>

> [!primary]
>
> By default, an app is launched with `1 GPU`. However, you can customize the resources you wish to use.
>

## Build you own apps and models to deploy

Below are examples of existing models that can be deployed with **AI Deploy**. However, you are free to deploy any other AI model or app of your choice.

### YOLO

**YOLO** ('You only look once'), is an `Object Detection` algorithms family.

*References:*

- YOLOv5 [repository](https://github.com/ultralytics/yolov5)
- YOLOv7 [repository](https://github.com/WongKinYiu/yolov7)
- Access and load YOLOv5 trained models from [PyTorch Hub](https://pytorch.org/hub/ultralytics_yolov5/)

### DALL-E mini

**DALL-E mini** is an AI model that can draw images from any text prompt (`Text-to-Image`).

*References:*

- DALL-E mini [repository](https://github.com/borisdayma/dalle-mini)
- Test DALL-E mini on this [website](https://www.craiyon.com/)
- Access DALL-E mini model from [Hugging Face](https://huggingface.co/dalle-mini)

### Stable Diffusion

**Stable Diffusion** is `Text-to-Image` model that generates images from text.

*References:*

- Stable Diffusion [repository](https://github.com/CompVis/stable-diffusion)
- Stable Diffusion [website](https://stability.ai/blog/stable-diffusion-public-release)
- Access Stable Diffusion model from [Hugging Face](https://huggingface.co/spaces/stabilityai/stable-diffusion)

### EfficientNet

**EfficientNet** is a family of `Image Classification` models. There are eight different EfficientNet models (`b0` -> `b7`)

*References:*

- Access and load EfficientNet model from [PyTorch Hub](https://pytorch.org/hub/nvidia_deeplearningexamples_efficientnet/)

### ResNet

**ResNet** are AI models based residual neural network whose aim is to solve `Image Classification` tasks.

*References:*

- Access and load ResNet models from [PyTorch Hub](https://pytorch.org/hub/pytorch_vision_resnet/)

### MobileNet V2

**MobileNet** are `Computer Vision` models designed to be used in mobile applications. They are known for their small size and low latency.

*References:*

- Access and load ResNet models from [PyTorch Hub](https://pytorch.org/hub/pytorch_vision_mobilenet_v2/)

### GPT-2

**GPT-2** is a `Text Generation` model developed by Open AI.

*References:*

- Find more information about GPT-2 [here](https://en.wikipedia.org/wiki/GPT-2)
- Access GPT-2 model from [Hugging Face](https://huggingface.co/docs/transformers/main/en/model_doc/gpt2)

### BERT

Famous NLP models based on **BERT** can also be deployed for `Text Classification` for example.

*References:*

- Access BERT-based models from [Hugging Face](https://huggingface.co/docs/transformers/main/en/model_doc/bert)

### BART

**BART**-based models can also be deployed for `Zero-Shot Classification` tasks.

*References:*

- Access BART-based models from [Hugging Face](https://huggingface.co/docs/transformers/main/en/model_doc/bart)

## Go further

You can also refer to our [GitHub repository](https://github.com/ovh/ai-training-examples) to find examples of AI apps to deploy.

> [!primary]
>
> You will find all the **codes** and **documentation** needed to deploy each app [here](/products/public-cloud-ai-and-machine-learning).
>

Here are some examples of AI apps we propose:

- Deploy an app for audio classification task using Streamlit
- Deploy a web service for YOLOv5 using Flask
- Deploy a Gradio app for sketch recognition
- Deploy an app for sentiment analysis with Hugging Face models using Flask
- Deploy an interactive app for EDA and prediction using Streamlit
- Deploy and call a spam classifier with FastAPI

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/en-gb/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

## Feedback

Please feel free to send us your questions, feedback and suggestions to help our team improve the service on the OVHcloud [Discord server](https://discord.gg/ovhcloud)

