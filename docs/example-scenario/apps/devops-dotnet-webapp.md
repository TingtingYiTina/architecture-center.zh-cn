---
title: 将 CI/CD 管道与 Azure DevOps 配合使用
description: 使用 Azure DevOps 生成 .NET 应用并将其发布到 Azure Web 应用。
author: christianreddington
ms.date: 07/11/18
ms.openlocfilehash: 97f16b2d3d9c15bc6f5db6fad4c9d8097243ad3d
ms.sourcegitcommit: 0a31fad9b68d54e2858314ca5fe6cba6c6b95ae4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2018
ms.locfileid: "51610781"
---
# <a name="cicd-pipeline-with-azure-devops"></a>将 CI/CD 管道与 Azure DevOps 配合使用

DevOps 集成了开发、质量保证和 IT 运营。 DevOps 要求通过统一的区域性和一系列严格的流程来交付软件。

本示例方案演示了开发团队如何使用 Azure DevOps 将 .NET 双层 Web 应用程序部署到 Azure 应用服务。 此 Web 应用程序依赖于下游的 Azure 平台即服务 (PaaS) 服务。 本文档还指出了在使用 Azure PaaS 设计此类方案时应考虑的一些注意事项。

采用现代的方法通过持续集成和持续部署 (CI/CD) 进行应用程序开发，你可以通过可靠的生成、测试、部署和监视服务更快地为用户带来价值。 将 Azure DevOps 等平台与应用服务等 Azure 服务配合使用，组织可将工作重心放在开发方案而不是管理支持性基础结构上。

## <a name="relevant-use-cases"></a>相关用例

以下用例可以考虑 DevOps：

* 加速应用程序开发和开发生命周期
* 将质量和一致性管理内置到自动化的生成和发布过程中

## <a name="architecture"></a>体系结构

![从体系结构的角度概要说明某个使用 Azure DevOps 和 Azure 应用服务的 DevOps 方案中涉及的 Azure 组件][architecture]

此方案包括一个使用 Azure DevOps 的 .NET Web 应用程序 CI/CD 管道。 数据流经方案的情形如下所示：

1. 更改应用程序源代码。
2. 提交应用程序代码和 Web 应用 web.config 文件。
3. 持续集成触发应用程序生成和单元测试。
4. 持续部署触发器使用特定于环境的参数化配置值来协调应用程序项目的部署。
5. 部署到 Azure 应用服务。
6. Azure Application Insights 收集并分析运行状况、性能和使用情况数据。
7. 查看运行状况、性能和使用情况信息。

### <a name="components"></a>组件

* [Azure DevOps][vsts] 服务用于管理端到端的开发生命周期 &mdash; 从规划和项目管理，到代码管理，再到生成和发布。
* [Azure Web 应用][web-apps]是用于托管 Web 应用程序、REST API 和移动后端的 PaaS 服务。 虽然本文着重讨论 .NET，但系统也支持多个其他的开发平台选项。
* [Application Insights][application-insights] 是第一方的可扩展应用程序性能管理 (APM) 服务，适用于多个平台上的 Web 开发人员。

### <a name="alternative-devops-tooling-options"></a>替代 DevOps 工具选项

虽然本文将重点放在 Azure DevOps 上，但也可以在本地改用 [Team Foundation Server][team-foundation-server]。 或者，也可以使用一组技术来取代使用 [Jenkins][jenkins-on-azure] 的开源开发管道。

从基础结构即代码的角度看，可将 [Azure 资源管理器模板][arm-templates]包含在 Azure DevOps 项目中，但也可考虑使用 [Terraform][terraform] 或 [Chef][chef]。 如果首选以基础结构即服务 (IaaS) 为基础的部署并且需要配置管理，可以考虑 [Azure Automation State Configuration][desired-state-configuration]、[Ansible][ansible] 或 [Chef][chef]。

### <a name="alternatives-to-azure-web-apps"></a>Azure Web 应用的替代方案

可以考虑使用以下替代方案在 Azure Web 应用中进行托管：

* [Azure 虚拟机][compare-vm-hosting] &mdash; 所适用的工作负荷需要进行严格的控制或者依赖于 OS 组件和服务，而后者 Web 应用无法提供（例如 Windows GAC 或 COM）。
* [Service Fabric][service-fabric] &mdash; 如果工作负荷体系结构侧重于分布式组件，而此类组件适合在严格控制的群集上部署和运行，则可使用此选项。 Service Fabric 也可用于托管容器。
* [Azure Functions][azure-functions] - 如果工作负荷体系结构侧重于精细的分布式组件，几乎不需要依赖，只在需要的情况下运行单个组件（不需持续运行），且不需对组件的运行进行协调，则 Azure Functions 是一种有效的无服务器方法。

选择适当的迁移路径时，此[决策树](/azure/architecture/guide/technology-choices/compute-decision-tree)可能有所帮助。

### <a name="devops"></a>DevOps

**[持续集成 (CI)][continuous-integration]** 维护稳定的版本，可让多个开发人员定期提交对共享代码库进行的小规模、经常性的更改。 在进行持续集成管道操作时，应遵循以下要求：
* 经常提交小规模的代码更改。 避免分批提交大规模或较复杂的更改，否则可能会使成功合并变得更困难。
* 使用足够大的代码覆盖率对应用程序组件展开单元测试，包括测试异常路径。
* 确保针对共享的主要（或主干）分支运行生成。 此分库应该稳定且始终处于“准备部署”状态。 不完整的或者正在进行的更改应该置于单独的可以频繁进行“前向集成”式合并的分库中，避免以后发生冲突。

**[持续交付 (CD)][continuous-delivery]** 不仅要展示稳定的版本，而且要展示稳定的部署。 这样会使得 CD 的实现更为困难一些，既需进行特定于环境的配置，又需通过某个机制来确保这些值设置正确。 其他 CD 注意事项包括：
* 需要足够的集成测试覆盖率，以验证是否以端到端的方式正确配置和运行了各个组件。
* CD 可能还需要设置和重置特定于环境的数据，以及管理数据库架构版本。
* 持续交付还应该扩展到负载测试和用户验收测试环境。
* 持续交付得益于理想情况下对所有环境进行的持续监视。
* 可以编写脚本来创建和配置托管基础结构，以便更轻松地确保跨环境的部署和集成测试的一致性与可靠性。 对于基于云的工作负荷而言，这可以大大简化操作。 有关详细信息，请参阅[基础结构即代码][infra-as-code]。
* 在项目生命周期中尽早开始持续交付。 开始得越晚，整合就越困难。
* 集成和单元测试的优先级应与应用程序功能相同。
* 使用与环境无关的部署包，在发布过程中管理特定于环境的配置。
* 在发布管理工具中保护敏感配置，或者通过在发布过程中调用硬件安全模块 (HSM) 或 [Azure Key Vault][azure-key-vault] 来这样做。 请勿在源代码管理中存储敏感配置。

**持续学习**。 使用 [Application Insights][application-insights] 等应用程序性能监视 (APM) 工具能够最有效地监视 CD 环境。 若要了解 Bug 或负载下的性能，必须针对应用程序工作负荷进行够深入的监视。 可将 Application Insights 集成到 VSTS 中，以[持续监视 CD 管道][app-insights-cd-monitoring]。 可以通过这种方式启用自动进入下一阶段的功能（不需人工干预），或者启用在检测到警报的情况下自动回退的功能。

## <a name="considerations"></a>注意事项

### <a name="availability"></a>可用性

考虑在生成云应用程序时，利用[针对可用性的典型设计模式][design-patterns-availability]。

在适当的[应用服务 Web 应用程序参考体系结构][app-service-reference-architecture]中审核可用性注意事项

若要了解其他可用性主题，请参阅 Azure 体系结构中心的[可用性核对清单][availability]。

### <a name="scalability"></a>可伸缩性

生成云应用程序时，请弄清楚[针对可伸缩性的典型设计模式][design-patterns-scalability]。

在适当的[应用服务 Web 应用程序参考体系结构][app-service-reference-architecture]中审核可伸缩性注意事项

若要了解其他可伸缩性主题，请参阅 Azure 体系结构中心的[可伸缩性核对清单][scalability]。

### <a name="security"></a>安全

考虑在适当情况下利用[针对安全性的典型设计模式][design-patterns-security]。

在适当的[应用服务 Web 应用程序参考体系结构][app-service-reference-architecture]中审核安全性注意事项。

若需安全解决方案的通用设计指南，请参阅 [Azure 安全性文档][security]。

### <a name="resiliency"></a>复原

根据情况考虑实施[针对复原的典型设计模式][design-patterns-resiliency]。

可以在 Azure 体系结构中心找到许多[建议用于应用服务的做法][resiliency-app-service]。

若需可复原解决方案的通用设计指南，请参阅[设计适用于 Azure 的可复原应用程序][resiliency]。

## <a name="deploy-the-scenario"></a>部署方案

### <a name="prerequisites"></a>先决条件

* 必须已经有 Azure 帐户。 如果还没有 Azure 订阅，可以在开始前创建一个[免费帐户][azure-free-account]。
* 必须注册一个 Azure DevOps 组织。 有关详细信息，请参阅[快速入门：创建组织][vsts-account-create]。

### <a name="walk-through"></a>演练

在本方案中，我们将使用 Azure DevOps 项目创建 CI/CD 管道。

该 Azure DevOps 项目将部署应用服务计划、应用服务以及 App Insights 资源，并配置 Azure DevOps 项目。

部署 Azure DevOps 项目并完成生成后，请查看关联的代码更改、工作项和测试结果。 你会发现，测试结果并未显示，因为代码不包含任何需要运行的测试。

查看发布定义。 可以看到，发布管道已设置好，可将应用程序发布到开发环境中。 请注意，有一个从 **Drop** 生成项目设置的**持续部署触发器**，它可将内容自动发布到开发环境中。 在持续部署过程中，可能会看到跨多个环境的发布。 发布可以跨基础结构（使用基础结构即代码之类的技术），还可以部署所需的应用程序包以及任何配置后任务。

## <a name="additional-considerations"></a>其他注意事项

* 考虑利用在 VSTS 市场中提供的一个[词汇切分任务][vsts-tokenization]。
* 考虑通过[部署：Azure Key Vault][download-keyvault-secrets] VSTS 任务将机密从 Azure Key Vault 下载到发布中。 然后可将这些机密用作发布定义中的变量，这样可以避免将其存储在源代码管理中。
* 考虑在发布定义中使用[发布变量][vsts-release-variables]来驱动对环境的配置更改。 发布变量的作用域可以是整个发布，也可以是给定的环境。 将变量用于机密信息时，请确保选择挂锁图标。
* 考虑在发布管道中使用[部署入口][vsts-deployment-gates]。 这样就可以利用与外部系统（例如，事件管理系统或其他定制系统）关联的监视数据，以便确定是否应提升某个发布。
* 如果需要在发布管道中进行手动干预，请考虑使用[审批][vsts-approvals]功能。
* 考虑在发布管道中尽早使用 [Application Insights][application-insights] 和其他监视工具。 许多组织只在生产环境中开始监视；如果监视其他环境，则可以提前在开发过程中识别 Bug，避免生产环境中出现问题。

## <a name="pricing"></a>定价

Azure DevOps 成本取决于组织中需要访问权限的用户数和其他因素，例如，所需的并发生成/发布数，以及测试用户数。 有关详细信息，请参阅 [Azure DevOps 定价][vsts-pricing-page]。

* [Azure DevOps][vsts-pricing-calculator] 是可用于管理开发生命周期的服务。 它按月按用户收费。 可能存在其他费用，具体取决于所需的并发管道数，以及是否有其他测试用户，或者是否使用了基本的用户许可证。

## <a name="related-resources"></a>相关资源

* [什么是 DevOps？][devops-whatis]
* [Microsoft 中的 DevOps - 如何使用 Azure DevOps][devops-microsoft]
* [分步教程：将 DevOps 与 Azure DevOps 配合使用][devops-with-vsts]
* [DevOps 查检表][devops-checklist]
* [使用 Azure DevOps 项目创建用于 .NET 的 CI/CD 管道][devops-project-create]

<!-- links -->
[ansible]: /azure/ansible/
[application-insights]: /azure/application-insights/app-insights-overview
[app-service-reference-architecture]: ../../reference-architectures/app-service-web-app/basic-web-app.md
[azure-free-account]: https://azure.microsoft.com/free/?WT.mc_id=A261C142F
[arm-templates]: /azure/azure-resource-manager/resource-group-overview#template-deployment
[architecture]: ./media/architecture-devops-dotnet-webapp.png
[availability]: /azure/architecture/checklist/availability
[chef]: /azure/chef/
[design-patterns-availability]: /azure/architecture/patterns/category/availability
[design-patterns-resiliency]: /azure/architecture/patterns/category/resiliency
[design-patterns-scalability]: /azure/architecture/patterns/category/performance-scalability
[design-patterns-security]: /azure/architecture/patterns/category/security
[desired-state-configuration]: /azure/automation/automation-dsc-overview
[devops-microsoft]: /azure/devops/devops-at-microsoft/
[devops-with-vsts]: https://almvm.azurewebsites.net/labs/vsts/
[devops-checklist]: /azure/architecture/checklist/dev-ops
[application-insights]: https://azure.microsoft.com/services/application-insights/
[cloud-based-load-testing]: https://visualstudio.microsoft.com/team-services/cloud-load-testing/
[cloud-based-load-testing-on-premises]: /vsts/test/load-test/clt-with-private-machines?view=vsts
[jenkins-on-azure]: /azure/jenkins/
[devops-whatis]: /azure/devops/what-is-devops
[download-keyvault-secrets]: /vsts/pipelines/tasks/deploy/azure-key-vault?view=vsts
[resource-groups]: /azure/azure-resource-manager/resource-group-overview
[resiliency-app-service]: /azure/architecture/checklist/resiliency-per-service#app-service
[resiliency]: /azure/architecture/checklist/resiliency
[scalability]: /azure/architecture/checklist/scalability
[vsts]: /vsts/?view=vsts#pivot=services
[continuous-integration]: /azure/devops/what-is-continuous-integration
[continuous-delivery]: /azure/devops/what-is-continuous-delivery
[web-apps]: /azure/app-service/app-service-web-overview
[terraform]: /azure/terraform/
[vsts-account-create]: /azure/devops/organizations/accounts/create-organization-msa-or-work-student?view=vsts
[vsts-approvals]: /vsts/pipelines/release/approvals/approvals?view=vsts
[devops-project]: https://portal.azure.com/?feature.customportal=false#create/Microsoft.AzureProject
[vsts-deployment-gates]: /vsts/pipelines/release/approvals/gates?view=vsts
[vsts-pricing-calculator]: https://azure.com/e/498aa024454445a8a352e75724f900b1
[vsts-pricing-page]: https://azure.microsoft.com/pricing/details/visual-studio-team-services/
[vsts-release-variables]: /vsts/pipelines/release/variables?view=vsts&tabs=batch
[vsts-tokenization]: https://marketplace.visualstudio.com/search?term=token&target=VSTS&category=All%20categories&sortBy=Relevance
[azure-key-vault]: /azure/key-vault/key-vault-overview
[infra-as-code]: https://blogs.msdn.microsoft.com/mvpawardprogram/2018/02/13/infrastructure-as-code/
[team-foundation-server]: https://visualstudio.microsoft.com/tfs/
[infra-as-code]: https://blogs.msdn.microsoft.com/mvpawardprogram/2018/02/13/infrastructure-as-code/
[service-fabric]: /azure/service-fabric/
[azure-functions]: /azure/azure-functions/
[azure-containers]: https://azure.microsoft.com/overview/containers/
[compare-vm-hosting]: /azure/app-service/choose-web-site-cloud-service-vm
[app-insights-cd-monitoring]: /azure/application-insights/app-insights-vsts-continuous-monitoring
[azure-region-pair-bcdr]: /azure/best-practices-availability-paired-regions
[devops-project-create]: /azure/devops-project/azure-devops-project-aspnet-core
[security]: /azure/security/