---
title: "Docker already runs on EC2, so why does Amazon ECS exist?"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

When learning AWS, I started with Amazon EC2. After deploying a project in Docker on one EC2 instance, I initially thought that deployment only required SSH, pulling a new image, and restarting the container.

However, many AWS architectures use Amazon ECS rather than only running Docker commands directly on EC2. This raised a question: if Docker already runs on EC2, why is Amazon ECS needed?

## Docker and ECS solve different problems

Docker packages an application and its dependencies into an image so it can run consistently across environments.

As the workload grows, operations may require:

- Maintaining a desired number of containers.
- Replacing a failed workload.
- Scaling container count with demand.
- Distributing requests through a load balancer.
- Rolling out new versions with less interruption.
- Observing many containers without logging in to every host.

These are **container orchestration** concerns rather than container packaging concerns.

Amazon ECS is a managed container orchestration service. Instead of manually running Docker commands on each host, an operator declares configuration and desired state, while the ECS scheduler helps place and manage container workloads.

For example, when an ECS Service has `desiredCount = 3`, it attempts to maintain three running Tasks. If one Task stops or becomes unhealthy, the Service scheduler can start a replacement.

## Where do ECS containers run?

Two common choices are:

- **Amazon EC2:** containers run on EC2 instances registered with the ECS cluster. The team manages EC2 capacity while ECS manages workloads.
- **AWS Fargate:** serverless compute for containers, removing direct server management.

ECS therefore does not replace Docker and does not necessarily replace EC2. Docker builds images; EC2 or Fargate provides compute; ECS orchestrates container deployment and operation.

## When is Docker directly on EC2 still reasonable?

For a small project with one container, infrequent changes, and acceptable manual operations, direct Docker on EC2 can be simpler. This is also the current production state of my Cloud E-Wallet project.

When the system needs multiple containers, self-recovery, rolling deployment, load balancing, or scaling, ECS becomes more useful because it centralizes desired-state management and reduces manual work.

## Conclusion

Docker and ECS complement each other:

- **Docker:** packages and runs containers.
- **Amazon ECS:** deploys, manages, and orchestrates containers as a system.

This distinction explains why an application can begin with Docker on EC2 and later evaluate ECS as operational requirements grow.

## References

- [Amazon ECS Developer Guide](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)
- [Post in AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2224875461610747/)

