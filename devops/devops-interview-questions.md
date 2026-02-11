# DevOps Interview Questions & Answers

## 1. What is DevOps?

**Answer:** DevOps is a culture, practice, and toolset that combines software development (Dev) and IT operations (Ops) to shorten development lifecycle and deliver high-quality software continuously.

**Key Principles:**
- **Collaboration:** Dev and Ops work together
- **Automation:** Automate repetitive tasks
- **Continuous Integration/Delivery:** Frequent releases
- **Monitoring:** Continuous feedback
- **Rapid Recovery:** Quick problem resolution

**Benefits:**
- Faster deployment
- Better collaboration
- Improved quality
- Faster issue resolution
- Greater efficiency

---

## 2. What is the difference between DevOps and Agile?

**Answer:**

| Feature | Agile | DevOps |
|---------|-------|--------|
| Focus | Development methodology | Deployment and operations |
| Scope | Software development | End-to-end (dev + ops) |
| Team | Development team | Dev + Ops + QA |
| Goal | Iterative development | Continuous delivery |
| Approach | Sprints and iterations | Automation and collaboration |
| Feedback | From users | From monitoring tools |

**Relationship:** DevOps extends Agile beyond development to include operations.

---

## 3. What is CI/CD?

**Answer:** CI/CD automates software delivery pipeline.

**CI (Continuous Integration):**
- Developers merge code frequently (multiple times/day)
- Automated build and testing
- Early bug detection
- Faster feedback

**CD (Continuous Delivery):**
- Code always in deployable state
- Manual deployment approval
- Automated testing

**CD (Continuous Deployment):**
- Automatic deployment to production
- No manual intervention
- Every passing build goes live

**Interview Tip:** CI/CD reduces manual work and speeds up release cycle.

---

## 4. What is the difference between Continuous Delivery and Continuous Deployment?

**Answer:**

**Continuous Delivery:**
- Code ready for production
- **Manual** deployment decision
- Human approval required
- Common in enterprise

**Continuous Deployment:**
- **Automatic** deployment to production
- No human intervention
- Every change goes live automatically
- Requires high confidence in tests

**Interview Tip:** Delivery = can deploy anytime, Deployment = auto-deployed.

---

## 5. What is Docker?

**Answer:** Docker is a platform for developing, shipping, and running applications in containers.

**Key Concepts:**
- **Container:** Lightweight, standalone package with application and dependencies
- **Image:** Template for creating containers
- **Dockerfile:** Instructions to build image
- **Docker Hub:** Repository for images

**Benefits:**
- Consistent environments
- Isolation
- Portability
- Lightweight (vs VMs)
- Fast startup

**Interview Tip:** Containers package everything needed to run application.

---

## 6. What is the difference between Docker and Virtual Machine?

**Answer:**

| Feature | Docker (Container) | Virtual Machine |
|---------|-------------------|-----------------|
| Architecture | Shares host OS kernel | Full OS per VM |
| Size | Lightweight (MBs) | Heavy (GBs) |
| Startup | Seconds | Minutes |
| Performance | Near-native | Slower |
| Isolation | Process-level | Hardware-level |
| Resource Usage | Less | More |
| Portability | High | Medium |

**Interview Tip:** Containers share OS kernel, VMs include full OS copy.

---

## 7. What is Kubernetes?

**Answer:** Kubernetes (K8s) is an open-source container orchestration platform for automating deployment, scaling, and management of containerized applications.

**Key Features:**
- **Auto-scaling:** Scale based on demand
- **Self-healing:** Replace failed containers
- **Load balancing:** Distribute traffic
- **Rolling updates:** Zero-downtime deployments
- **Service discovery:** Find services automatically

**Components:**
- **Pod:** Smallest unit (one or more containers)
- **Node:** Worker machine
- **Cluster:** Set of nodes
- **Service:** Expose pods to network
- **Deployment:** Manage pod replicas

---

## 8. What is the difference between Docker Swarm and Kubernetes?

**Answer:**

| Feature | Docker Swarm | Kubernetes |
|---------|--------------|------------|
| Complexity | Simple | Complex |
| Learning Curve | Easy | Steep |
| Scalability | Good | Excellent |
| Community | Smaller | Larger |
| Auto-scaling | Basic | Advanced |
| Setup | Quick | Slower |
| Use Case | Small to medium | Large, enterprise |

**Interview Tip:** Swarm for simplicity, Kubernetes for powerful features.

---

## 9. What is Infrastructure as Code (IaC)?

**Answer:** IaC is managing and provisioning infrastructure through code instead of manual processes.

**Benefits:**
- Version control
- Consistency
- Reusability
- Faster deployment
- Documentation

**Popular Tools:**
- **Terraform:** Multi-cloud provisioning
- **Ansible:** Configuration management
- **CloudFormation:** AWS infrastructure
- **Puppet/Chef:** Configuration management

**Interview Tip:** Treat infrastructure like application code - version-controlled and automated.

---

## 10. What is Jenkins?

**Answer:** Jenkins is an open-source automation server for CI/CD.

**Features:**
- **Build automation:** Compile, test, deploy
- **Plugins:** 1500+ plugins for integration
- **Pipeline:** Define CI/CD as code
- **Distributed builds:** Use multiple machines
- **Scheduling:** Trigger builds automatically

**Key Concepts:**
- **Job:** Task to execute
- **Build:** Execution of job
- **Pipeline:** Series of automated steps
- **Agent:** Machine executing job

---

## 11. What is a Jenkins Pipeline?

**Answer:** Jenkins Pipeline is suite for defining CI/CD pipeline as code.

**Types:**

**Declarative Pipeline:**
- Structured syntax
- Easier for beginners
- More restrictions

**Scripted Pipeline:**
- Groovy-based
- More flexible
- Complex logic

**Benefits:**
- Version controlled (Jenkinsfile)
- Code review
- Reusable
- Better visibility

---

## 12. What is Ansible?

**Answer:** Ansible is an open-source automation tool for configuration management, application deployment, and task automation.

**Key Features:**
- **Agentless:** No software on managed nodes
- **YAML:** Simple playbook syntax
- **Idempotent:** Same result on multiple runs
- **Push-based:** Control node pushes to managed nodes

**Components:**
- **Playbook:** YAML file with tasks
- **Inventory:** List of managed hosts
- **Module:** Unit of work
- **Role:** Reusable set of tasks

---

## 13. What is the difference between Ansible and Terraform?

**Answer:**

| Feature | Ansible | Terraform |
|---------|---------|-----------|
| Purpose | Configuration management | Infrastructure provisioning |
| Type | Mutable | Immutable |
| Language | YAML | HCL (HashiCorp Configuration Language) |
| State | No state file | State file |
| Approach | Procedural | Declarative |
| Best For | Configure existing | Create new infrastructure |

**Together:** Use Terraform to provision, Ansible to configure.

---

## 14. What is Git in DevOps?

**Answer:** Git is distributed version control system essential for DevOps.

**Role in DevOps:**
- Source code management
- Collaboration
- Version tracking
- Branch strategies
- Integration with CI/CD

**DevOps Practices:**
- **Branching strategies:** Gitflow, Trunk-based
- **Code review:** Pull requests
- **Automation:** Webhooks trigger CI/CD
- **Version tracking:** Tags for releases

---

## 15. What is Monitoring in DevOps?

**Answer:** Monitoring tracks application and infrastructure performance to ensure reliability.

**Types:**

**Infrastructure Monitoring:**
- CPU, memory, disk usage
- Tools: Nagios, Zabbix

**Application Monitoring:**
- Performance, errors, user experience
- Tools: New Relic, AppDynamics

**Log Monitoring:**
- Collect and analyze logs
- Tools: ELK Stack, Splunk

**Key Metrics:**
- Response time
- Error rates
- Resource utilization
- Availability

---

## 16. What is the ELK Stack?

**Answer:** ELK Stack is collection of three open-source tools for log management.

**Components:**

**Elasticsearch:**
- Search and analytics engine
- Stores and indexes data

**Logstash:**
- Log collection and processing
- Transforms data

**Kibana:**
- Visualization and dashboards
- Query and explore data

**Use Cases:**
- Centralized logging
- Log analysis
- Real-time monitoring
- Security analytics

---

## 17. What is Prometheus?

**Answer:** Prometheus is open-source monitoring and alerting toolkit.

**Features:**
- **Time-series database:** Metric storage
- **Pull model:** Scrapes metrics from targets
- **PromQL:** Query language
- **Alerting:** Alert manager for notifications
- **Grafana integration:** Visualization

**Use Cases:**
- Infrastructure monitoring
- Application metrics
- Kubernetes monitoring

---

## 18. What is Container Orchestration?

**Answer:** Container orchestration automates deployment, management, scaling, and networking of containers.

**Tasks:**
- Container deployment
- Load balancing
- Scaling up/down
- Health monitoring
- Service discovery
- Networking

**Tools:**
- Kubernetes (most popular)
- Docker Swarm
- Apache Mesos

---

## 19. What is a Microservices Architecture?

**Answer:** Microservices is architectural style where application is collection of small, independent services.

**Characteristics:**
- **Independent:** Each service standalone
- **Focused:** Single business capability
- **Decentralized:** No central database
- **Independently deployable:** Deploy without affecting others

**Benefits:**
- Scalability
- Flexibility
- Technology diversity
- Fault isolation

**Challenges:**
- Complexity
- Distributed system issues
- Testing difficulty

**vs Monolithic:** Monolith is single unit, microservices are multiple independent services.

---

## 20. What is Blue-Green Deployment?

**Answer:** Blue-Green deployment is strategy with two identical production environments.

**Process:**
1. **Blue:** Current production version
2. **Green:** New version deployed
3. Test green environment
4. Switch traffic from blue to green
5. Keep blue as backup
6. If issues, switch back to blue

**Benefits:**
- Zero downtime
- Quick rollback
- Reduced risk

**Drawback:** Requires double infrastructure

---

## 21. What is Canary Deployment?

**Answer:** Canary deployment gradually rolls out changes to small subset of users before full deployment.

**Process:**
1. Deploy new version to small percentage (e.g., 5%)
2. Monitor metrics
3. If stable, increase percentage
4. Eventually 100% on new version

**Benefits:**
- Early issue detection
- Reduced blast radius
- Gradual rollout

**Named after:** Coal mine canaries (early warning system)

---

## 22. What is Rolling Deployment?

**Answer:** Rolling deployment gradually replaces old version with new version.

**Process:**
1. Update one instance at a time
2. Wait for health check
3. Move to next instance
4. Repeat until all updated

**Benefits:**
- No downtime
- Gradual rollout
- Can pause/rollback

**Drawback:** Two versions running simultaneously (briefly)

---

## 23. What is Configuration Management?

**Answer:** Configuration management maintains system state and consistency across infrastructure.

**Tools:**
- **Ansible:** Agentless, push-based
- **Puppet:** Agent-based, pull-based
- **Chef:** Agent-based, pull-based
- **SaltStack:** Event-driven

**Benefits:**
- Consistency
- Automation
- Documentation
- Version control

---

## 24. What is Docker Compose?

**Answer:** Docker Compose is tool for defining and running multi-container Docker applications.

**Features:**
- Single YAML file (docker-compose.yml)
- Define multiple services
- Networking between containers
- Volume management
- Environment variables

**Common Commands:**
- `docker-compose up` - Start services
- `docker-compose down` - Stop services
- `docker-compose ps` - List services

**Use Case:** Local development with multiple containers

---

## 25. What is a Load Balancer?

**Answer:** Load balancer distributes network traffic across multiple servers.

**Benefits:**
- High availability
- Scalability
- No single point of failure
- Better resource utilization

**Types:**

**Layer 4 (Network):**
- Based on IP and port
- Faster

**Layer 7 (Application):**
- Based on content (URL, headers)
- More intelligent routing

**Tools:** Nginx, HAProxy, AWS ELB

---

## 26. What is Continuous Monitoring?

**Answer:** Continuous monitoring tracks application and infrastructure in real-time.

**Aspects:**
- **Performance:** Response times, throughput
- **Availability:** Uptime monitoring
- **Security:** Threat detection
- **Logs:** Error tracking
- **User Experience:** Real user monitoring

**Benefits:**
- Early issue detection
- Proactive problem solving
- Data-driven decisions
- Improved reliability

---

## 27. What is GitOps?

**Answer:** GitOps uses Git as single source of truth for declarative infrastructure and applications.

**Principles:**
- **Declarative:** Desired state in Git
- **Versioned:** Git history
- **Automated:** Changes applied automatically
- **Observable:** Monitor actual vs desired state

**Workflow:**
1. Commit changes to Git
2. CI/CD pipeline triggered
3. Changes deployed automatically
4. System reconciles state

**Benefits:**
- Version control
- Audit trail
- Easy rollback
- Collaboration

---

## 28. What is the difference between DevOps and SRE?

**Answer:**

| Feature | DevOps | SRE (Site Reliability Engineering) |
|---------|--------|-----------------------------------|
| Origin | Cultural movement | Google's approach |
| Focus | Development + Operations | Reliability and operations |
| Goals | Faster delivery | Reliability and uptime |
| Approach | Broad principles | Specific practices |
| Metrics | Deployment frequency | SLIs, SLOs, SLAs |
| Error Budgets | Not defined | Core concept |

**Relationship:** SRE implements DevOps principles with specific prescriptions.

---

## 29. What is a Service Mesh?

**Answer:** Service mesh is infrastructure layer for handling service-to-service communication in microservices.

**Features:**
- Load balancing
- Service discovery
- Encryption (mTLS)
- Monitoring and tracing
- Circuit breaking
- Rate limiting

**Popular Tools:**
- **Istio:** Most feature-rich
- **Linkerd:** Lightweight
- **Consul Connect:** HashiCorp

**Benefits:**
- Centralized control
- Security
- Observability

---

## 30. What are DevOps Best Practices?

**Answer:**

**1. Automation:**
- Automate testing, deployment, infrastructure

**2. Version Control:**
- Everything in Git (code, configs, scripts)

**3. Continuous Integration:**
- Frequent code integration and testing

**4. Continuous Delivery:**
- Always deployment-ready

**5. Monitoring and Logging:**
- Comprehensive observability

**6. Collaboration:**
- Break down silos between teams

**7. Security (DevSecOps):**
- Integrate security early

**8. Small, Frequent Releases:**
- Reduce risk per release

**9. Infrastructure as Code:**
- Version-controlled infrastructure

**10. Feedback Loops:**
- Learn and improve continuously

**Interview Tip:** DevOps is culture and mindset, not just tools.

---
## 31. What is Infrastructure as Code (IaC)?

**Answer:** IaC manages infrastructure through code instead of manual processes.

**Benefits:**
- Version control
- Repeatability
- Consistency
- Faster provisioning
- Reduced errors
- Documentation

**Tools:**
- **Terraform:** Multi-cloud provisioning
- **Ansible:** Configuration management
- **CloudFormation:** AWS-specific
- **Pulumi:** Programming languages

**Approaches:** Declarative (what) vs Imperative (how)

---

## 32. What is Configuration Management?

**Answer:** Configuration Management automates server configuration and maintenance.

**Tools:**
- **Ansible:** Agentless, YAML-based
- **Puppet:** Agent-based, declarative
- **Chef:** Agent-based, Ruby DSL
- **SaltStack:** Agent or agentless

**Benefits:**
- Consistency across environments
- Automated deployments
- Reduced human error
- Scalability

---

## 33. What is a container?

**Answer:** Container packages application with dependencies into isolated unit.

**Characteristics:**
- Lightweight
- Portable
- Isolated
- Fast startup
- Shares OS kernel

**vs Virtual Machines:**
- Containers: Share kernel, faster, smaller
- VMs: Full OS, more isolation, heavier

**Platform:** Docker is most popular container platform

---

## 34. What is Docker?

**Answer:** Docker is platform for developing, shipping, and running applications in containers.

**Components:**
- **Docker Engine:** Runtime
- **Docker Hub:** Image registry
- **Dockerfile:** Build instructions
- **Docker Compose:** Multi-container applications

**Workflow:**
1. Write Dockerfile
2. Build image
3. Run container

**Benefits:** "Build once, run anywhere"

---

## 35. What is Kubernetes?

**Answer:** Kubernetes (K8s) is container orchestration platform.

**Features:**
- Automated deployment
- Scaling
- Load balancing
- Self-healing
- Rolling updates
- Service discovery

**Components:**
- **Pods:** Smallest deployable units
- **Services:** Network abstraction
- **Deployments:** Desired state management
- **Nodes:** Worker machines

**Use Case:** Managing containerized applications at scale

---

## 36. What is a microservices architecture?

**Answer:** Microservices break application into small, independent services.

**Characteristics:**
- Single responsibility
- Independently deployable
- Own database
- Loosely coupled
- Technology agnostic

**Benefits:**
- Scalability
- Flexibility
- Fault isolation
- Faster development

**Challenges:** Complexity, distributed system issues, monitoring

---

## 37. What is Blue-Green Deployment?

**Answer:** Blue-Green deployment runs two identical production environments.

**Process:**
1. Blue environment serves production
2. Deploy new version to Green
3. Test Green environment
4. Switch traffic to Green
5. Blue becomes standby

**Benefits:**
- Zero downtime
- Easy rollback
- Reduced risk

**Requirement:** Infrastructure to run two environments

---

## 38. What is Canary Deployment?

**Answer:** Canary deployment gradually rolls out changes to subset of users.

**Process:**
1. Deploy to small percentage (e.g., 5%)
2. Monitor metrics
3. Gradually increase percentage
4. Rollback if issues found
5. Full deployment if successful

**Benefits:**
- Early issue detection
- Limited blast radius
- Risk mitigation

---

## 39. What is monitoring and observability?

**Answer:**

**Monitoring:**
- Collecting predefined metrics
- Alerts on known issues
- Health checks

**Observability:**
- Understanding system from outputs
- Discover unknown issues
- Three pillars: Logs, Metrics, Traces

**Tools:**
- **Prometheus:** Metrics collection
- **Grafana:** Visualization
- **ELK Stack:** Logging (Elasticsearch, Logstash, Kibana)
- **Jaeger:** Distributed tracing

---

## 40. What is a load balancer?

**Answer:** Load balancer distributes network traffic across multiple servers.

**Types:**
- **Layer 4 (Transport):** Based on IP/port
- **Layer 7 (Application):** Based on content

**Algorithms:**
- Round Robin
- Least Connections
- IP Hash
- Weighted distribution

**Benefits:** High availability, scalability, failover

**Tools:** Nginx, HAProxy, AWS ELB, Azure Load Balancer

---

## 41. What is high availability?

**Answer:** High availability ensures system operates continuously without failure.

**Measured by:** Uptime percentage (99.9% = "three nines")

**Techniques:**
- Redundancy
- Load balancing
- Failover
- Health checks
- Automated recovery
- Geographic distribution

**Target:** 99.999% (five nines) = 5.26 minutes downtime/year

---

## 42. What is disaster recovery?

**Answer:** Disaster recovery is plan to restore systems after catastrophic failure.

**Metrics:**
- **RTO (Recovery Time Objective):** Maximum downtime
- **RPO (Recovery Point Objective):** Maximum data loss

**Strategies:**
- Backup and restore
- Pilot light
- Warm standby
- Hot site/Active-Active

**Components:** Backups, documentation, testing, communication plan

---

## 43. What is GitOps?

**Answer:** GitOps uses Git as single source of truth for infrastructure and applications.

**Principles:**
- Declarative configuration
- Git as source of truth
- Automated deployment
- Continuous reconciliation

**Benefits:**
- Version control
- Audit trail
- Easy rollback
- Collaboration

**Tools:** ArgoCD, Flux, Jenkins X

---

## 44. What is observability?

**Answer:** Observability measures how well you can understand system's internal state from external outputs.

**Three Pillars:**
- **Logs:** Discrete events
- **Metrics:** Numeric measurements over time
- **Traces:** Request flow through system

**Benefits:**
- Debug production issues
- Understand system behavior
- Optimize performance
- Capacity planning

**Tools:** Datadog, New Relic, Splunk, Honeycomb

---

## 45. What is Service Mesh?

**Answer:** Service mesh manages service-to-service communication in microservices.

**Features:**
- Service discovery
- Load balancing
- Encryption
- Authentication
- Monitoring
- Traffic management

**Components:**
- **Data Plane:** Proxies (Envoy)
- **Control Plane:** Configuration

**Popular Service Meshes:** Istio, Linkerd, Consul

**Use Case:** Complex microservices requiring advanced networking

---