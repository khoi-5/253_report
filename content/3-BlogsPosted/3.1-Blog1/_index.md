---
title: "Docker already runs on EC2, so why does Amazon ECS exist?"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

When learning AWS, I started with EC2.

After creating an EC2 instance and successfully deploying a project with Docker, I thought that was probably all there was to the deployment process. Whenever a new version was available, I would simply SSH into EC2, pull the new image, and restart the container.

However, while reviewing AWS reference architectures and documentation, I noticed that many systems use Amazon ECS instead of running Docker directly on EC2.

That made me wonder:

If Docker can already run on EC2, why did AWS develop Amazon ECS?

After researching the subject, I realized that Docker and ECS solve two entirely different problems.

Docker helps package an application into a container so that it can run in different environments.

As an application grows, however, new operational needs emerge:

- Maintaining a specified number of containers.
- Automatically restarting failed containers.
- Scaling the number of containers when traffic increases.
- Deploying new application versions more conveniently.

These are no longer Docker packaging concerns. They are container management and orchestration concerns.

That is the purpose of Amazon ECS (Elastic Container Service).

Simply put, ECS is an AWS service that helps manage running containers. Instead of SSHing into each EC2 instance and manually executing Docker commands, I declare the desired state of the system, and ECS helps maintain that state.

For example, if I want three backend containers to remain active, ECS can create a replacement when one container fails and stops, without requiring manual intervention.

While studying ECS, I also learned that it provides two deployment options:

- **EC2 Launch Type:** EC2 is still used, but ECS manages the containers running on those EC2 instances.
- **AWS Fargate:** there is no need to manage EC2 directly; the container configuration is declared, and AWS manages the underlying infrastructure.

What I find interesting is that ECS does not replace Docker.

Docker remains the tool used to create containers, while ECS helps manage those containers as the application grows and operations become more complex.

After reading the documentation, I understood why Docker and ECS often appear together in AWS architectures. One packages the application, while the other helps deploy and operate containers more effectively.

## References

- [Amazon Elastic Container Service Documentation](https://docs.aws.amazon.com/ecs/)

## Published post

- [View the post in AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2224875461610747/)