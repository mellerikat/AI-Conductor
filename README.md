# Welcome to AI Conductor !
AI Conductor is a cloud-based MLOps service for developing, registering, and managing AI Solutions to be supplied to AIOps. Key features of AI Conductor include:

- Integration and management of various AI Solutions
- Creation of Instances to optimize AI Models based on user data
- Support for AI Model training pipelines based on Kubeflow
- Provision of trained AI Models in conjunction with Edge AIOps

AI Conductor allows users to leverage verified AI Solutions from LG Electronics as well as register and utilize their own AI Solutions. This enables users with limited AI expertise to easily adopt high-quality AI Solutions, while users with AI skills can register their AI Solutions and utilize them in conjunction with Edge AIOps.

Additionally, AI Conductor uses a scalable Kubernetes-based model training infrastructure to efficiently train AI Models and supply them to Edge Conductor. By supplying AI Solutions to Edge AIOps, AI Conductor will lead the democratization and innovation of AI technology.

## Key Features

AI Conductor provides the following high-level features:

#### AI Solution

AI Solutions, incorporating proven analytical expertise and AI/ML technology from real industrial settings, are provided.

#### Instance

An Instance is a computing resource that handles tasks such as AI Model training and traffic balancing based on configured Model training execution environment information.

## Installation
> **Note**  
> You can skip `secrets-store-csi-driver` and `aws-secrets-manager` if they are already installed.

Add the required repositories (total of 3).
```bash
helm repo add secrets-store-csi-driver https://kubernetes-sigs.github.io/secrets-store-csi-driver/charts
helm repo add aws-secrets-manager https://aws.github.io/secrets-store-csi-driver-provider-aws
helm repo add mellerikat-aicond https://mellerikat.github.io/AI-Conductor
```

Verify that the repositories have been added correctly.
```bash
helm repo ls

NAME                            URL
secrets-store-csi-driver        https://kubernetes-sigs.github.io/secrets-store-csi-driver/charts
aws-secrets-manager             https://aws.github.io/secrets-store-csi-driver-provider-aws
mellerikat-aicond               https://mellerikat.github.io/AI-Conductor
```
Create a `values-file.yaml` file tailored to your environment by referring to `example-values.yaml`.

Install the required applications (total of 3).
```bash
helm install csi-secrets-store secrets-store-csi-driver/secrets-store-csi-driver --version 1.3.2
helm install secrets-provider-aws aws-secrets-manager/secrets-store-csi-driver-provider-aws -n kube-system
helm install ai-conductor mellerikat-aicond/ai-conductor --values {values-file.yaml} -n ai-conductor
```

# User Guide
- [AI Solution](https://mellerikat.com/user_guide/data_scientist_guide/ai_conductor/ai_solution)
- [Instance](https://mellerikat.com/user_guide/data_scientist_guide/ai_conductor/instance)
