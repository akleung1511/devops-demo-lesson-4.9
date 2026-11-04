# CI/CD Tool Selection — NTU Module 4.9

## 1. Types of CI/CD Tools

### 1.1 Platform-Integrated CI/CD

**Who runs it:**  
The Git platform provider operates the CI/CD service.

**Example tools:**
1. GitHub Actions
2. GitLab CI/CD

**When to choose it:**
1. When all source code is hosted on one Git platform.
2. When the team wants a simple setup without managing a separate CI server.
3. When developers want pipeline results integrated with commits and pull requests.

**Trade-offs:**
1. Pipelines are closely tied to the Git platform.
2. Moving to another Git platform may require rewriting workflow configurations.
3. The team depends on the Git platform's availability and supported capabilities.

### 1.2 Managed CI Service (SaaS)

**Who runs it:**  
A separate CI/CD service provider operates and maintains the CI infrastructure.

**Example tools:**
1. CircleCI
2. Travis CI

**When to choose it:**
1. When a team works across multiple supported Git platforms.
2. When the company wants a dedicated CI/CD service and dashboard.
3. When the team does not want to maintain its own CI servers.

**Trade-offs:**
1. Requires managing another vendor, account and integration.
2. Source code, build data and credentials may be processed by a third-party provider.
3. The team depends on the service provider's availability and supported integrations.


### 1.3 Self-Hosted CI/CD

**Who runs it:**  
The organisation's own IT or DevOps team installs, operates and maintains the CI/CD server on company-controlled infrastructure.

**Example tools:**
1. Jenkins
2. TeamCity

**When to choose it:**
1. When security or compliance requirements demand that code and builds remain on company-controlled infrastructure.
2. When the organisation needs extensive control over its build environment.
3. When specialised hardware or private-network access is required.

**Trade-offs:**
1. Requires dedicated people to install, configure and maintain the CI/CD servers.
2. The organisation must manage security patches, updates and backups.
3. Infrastructure maintenance increases operational workload.


## 2. CI/CD Tool Selection Decision Flow

```text
START
  |
  v
Must code and builds stay on company servers?
  |
  +-- YES --> Self-hosted
  |           Examples: Jenkins, TeamCity
  |
  +-- NO
       |
       v
     Is all code on one Git platform?
       |
       +-- YES --> Platform-integrated
       |           Examples: GitHub Actions, GitLab CI/CD
       |
       +-- NO
            |
            v
          Need one CI tool across Git platforms?
            |
            +-- YES --> Managed CI service (SaaS)
            |           Examples: CircleCI, Travis CI
            |
            +-- NO --> Review team requirements
                       and available resources
```

**Additional consideration:** Before selecting a tool,
check whether the organisation has engineers available
to operate and maintain its CI/CD infrastructure.


## 2. CI/CD Tool Selection Decision Flow

```text
START
  |
  v
Must code and builds stay on company servers?
  |
  +-- YES --> Self-hosted
  |           Examples: Jenkins, TeamCity
  |
  +-- NO
       |
       v
     Is all code on one Git platform?
       |
       +-- YES --> Platform-integrated
       |           Examples: GitHub Actions, GitLab CI/CD
       |
       +-- NO
            |
            v
          Need one CI tool across Git platforms?
            |
            +-- YES --> Managed CI service (SaaS)
            |           Examples: CircleCI, Travis CI
            |
            +-- NO --> Review team requirements
                       and available resources
```

**Additional consideration:** Before selecting a tool,
check whether the organisation has engineers available
to operate and maintain its CI/CD infrastructure.


### Scenario B — Healthcare Company

**Recommended type:** Self-hosted CI/CD  
**Recommended tool:** Jenkins

I recommend Jenkins because the healthcare company has strict data-protection requirements and cannot store its source code or build artifacts in a public cloud. Jenkins can be installed on the company's own infrastructure, allowing the organisation to control where its code, build processes and artifacts are stored. The company also has two dedicated DevOps engineers who can manage the CI/CD environment.

The main trade-offs are the additional maintenance workload and responsibility for security updates, backups and server reliability. Platform-integrated services such as standard cloud-hosted GitHub Actions are less suitable because of the company's data-residency restrictions. Managed SaaS services such as standard cloud-hosted CircleCI are also less suitable because they involve a third-party cloud service. A properly configured, fully self-hosted Jenkins environment is therefore the best fit.


### Scenario D — Software Consultancy

**Recommended type:** Managed CI Service (SaaS)  
**Recommended tool:** CircleCI

I recommend CircleCI because the consultancy manages projects across different Git platforms, including GitHub and Bitbucket. A managed CI service can provide a centralised CI/CD dashboard and consistent pipeline configuration across supported repositories. CircleCI also reduces infrastructure maintenance because the provider operates the hosted CI environment, allowing the consultancy's developers to focus on client projects.

The main trade-offs are dependence on a third-party CI provider and the need to manage integrations, credentials and client permissions. Platform-integrated tools such as GitHub Actions are less suitable because they are tied to their respective Git platforms, making a unified CI/CD approach more difficult. Self-hosted tools such as Jenkins could support multiple repositories but would require the consultancy to maintain its own CI infrastructure, which it explicitly wants to avoid.
