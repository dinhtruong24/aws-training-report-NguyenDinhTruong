---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Streamline and reinforce container security by advancing container build methods and establishing isolated network environments for production setups.
* Master advanced container management solutions by diving deep into Kubernetes and Amazon EKS, and evaluating strategic infrastructure choices (ECS vs EKS) based on project budgets and system scales.
* Embrace the DevOps philosophy by exploring AWS specialized developer suites to construct automated delivery pipelines, minimizing manual deployment errors.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| Monday  | - Implemented advanced Docker optimization; integrated Multi-stage Build techniques into the Dockerfile structure to split build environments from runtimes, discarding redundant dependencies to dramatically shrink the container image footprint.  | 08/06/2026 | 08/06/2026      | https://000015.awsstudygroup.com/ |
| Tuesday  | - Engineered advanced network topologies and access control on Amazon ECS; utilized the awsvpc network mode to assign an independent Elastic Network Interface (ENI) and private IP to each Task, while enforcing the least-privilege principle across Task Roles.  | 09/06/2026 | 09/06/2026      | https://000016.awsstudygroup.com/ https://000067.awsstudygroup.com/ https://000118.awsstudygroup.com/ https://000152.awsstudygroup.com/ |
| Wednesday  | - Explored the Kubernetes landscape and Amazon EKS capabilities; broke down the operational mechanics of the Control Plane, Worker Nodes, Pods, and Services, evaluating how EKS abstracts away cluster management complexities in the cloud. | 10/06/2026 | 10/06/2026      | https://000126.awsstudygroup.com/ |
| Thursday  | - Conducted a comprehensive architectural review comparing Amazon ECS against Amazon EKS; structured a comparative evaluation matrix assessing operational complexity, built-in features, and AWS integration to determine the optimal solution for specific production requirements.  | 11/06/2026 | 11/06/2026      | https://000065.awsstudygroup.com/ https://000126.awsstudygroup.com/ |
| Friday  | - Analyzed automation execution paths via the AWS Developer Tools suite; surveyed the end-to-end orchestration flow between AWS CodePipeline, CodeBuild, and CodeDeploy, covering source control tracking, automated testing, and release delivery.   | 12/06/2026 | 12/06/2026      | https://000017.awsstudygroup.com/ https://000023.awsstudygroup.com/ https://000080.awsstudygroup.com/ https://000136.awsstudygroup.com/ https://000112.awsstudygroup.com/ |
| Saturday  | - Devoted the entire session to programming the server-side (Backend) logic for the project's core multi-tenancy architecture module | 13/06/2026 | 13/06/2026      | https://cloudjourney.awsstudygroup.com/ |
### Week 6 Achievements:

* Slim & Secure Container Architecture: Successfully minimized Docker image sizes via Multi-stage builds and hardened microservices security perimeters by deploying the isolated awsvpc network mode for ECS tasks.

* Advanced Orchestration Blueprinting: Acquired a solid foundation in Kubernetes runtime concepts and successfully generated a strategic infrastructure analysis guide between ECS and EKS for corporate application modeling.

* Pipeline Automation & Core Delivery: Modeled an automated CI/CD blueprint utilizing native AWS developer tools and successfully finalized the core backend features for the project's Tenant-service on schedule.
 ### Week 6 Evaluation:
* While deploying the awsvpc network mode for ECS tasks on Tuesday, the system encountered a critical infrastructure bottleneck due to subnet IP address exhaustion, triggered by a rapid automatic scale-out of active tasks. This served as an incredibly valuable real-world lesson on the necessity of thorough initial CIDR block planning. I successfully mitigated the incident by re-architecting and routing dedicated secondary subnets tailored exclusively for ECS workloads, ensuring uninterrupted and safe elastic scaling capacities.
