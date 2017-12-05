---
title: "用于选择数据存储的条件"
description: "Azure 计算选项概述"
author: MikeWasson
ms.openlocfilehash: 7fb75cd334438c5b985fa04ad8afe3236f2391f8
ms.sourcegitcommit: b0482d49aab0526be386837702e7724c61232c60
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2017
---
# <a name="criteria-for-choosing-a-data-store"></a><span data-ttu-id="8bd52-103">用于选择数据存储的条件</span><span class="sxs-lookup"><span data-stu-id="8bd52-103">Criteria for choosing a data store</span></span>

<span data-ttu-id="8bd52-104">Azure 支持许多类型的数据存储解决方案，每个都提供了不同的特性和功能。</span><span class="sxs-lookup"><span data-stu-id="8bd52-104">Azure supports many types of data storage solutions, each providing different features and capabilities.</span></span> <span data-ttu-id="8bd52-105">本文介绍了在评估数据存储时应当使用的比较条件。</span><span class="sxs-lookup"><span data-stu-id="8bd52-105">This article describes the comparison criteria you should use when evaluating a data store.</span></span> <span data-ttu-id="8bd52-106">其目标是帮助你确定哪些数据存储类型可以满足你的解决方案的要求。</span><span class="sxs-lookup"><span data-stu-id="8bd52-106">The goal is to help you determine which data storage types can meet your solution's requirements.</span></span>

## <a name="general-considerations"></a><span data-ttu-id="8bd52-107">一般注意事项</span><span class="sxs-lookup"><span data-stu-id="8bd52-107">General Considerations</span></span>

<span data-ttu-id="8bd52-108">若要开始比较，请尽可能多地收集关于数据需求的以下信息。</span><span class="sxs-lookup"><span data-stu-id="8bd52-108">To start your comparison, gather as much of the following information as you can about your data needs.</span></span> <span data-ttu-id="8bd52-109">该信息可以帮助你确定哪些数据存储类型可满足需求。</span><span class="sxs-lookup"><span data-stu-id="8bd52-109">This information will help you to determine which data storage types will meet your needs.</span></span>

### <a name="functional-requirements"></a><span data-ttu-id="8bd52-110">功能要求</span><span class="sxs-lookup"><span data-stu-id="8bd52-110">Functional requirements</span></span>

- <span data-ttu-id="8bd52-111">**数据格式**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-111">**Data format**.</span></span> <span data-ttu-id="8bd52-112">打算存储什么类型的数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-112">What type of data are you intending to store?</span></span> <span data-ttu-id="8bd52-113">常见类型包括事务数据、JSON 对象、遥测、搜索索引或平面文件。</span><span class="sxs-lookup"><span data-stu-id="8bd52-113">Common types include transactional data, JSON objects, telemetry, search indexes, or flat files.</span></span>
- <span data-ttu-id="8bd52-114">**数据大小**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-114">**Data size**.</span></span> <span data-ttu-id="8bd52-115">需要存储的实体有多大？</span><span class="sxs-lookup"><span data-stu-id="8bd52-115">How large are the entities you need to store?</span></span> <span data-ttu-id="8bd52-116">这些实体是需要保持为单个文档，还是可以将它们拆分到多个文档、表和集合中？</span><span class="sxs-lookup"><span data-stu-id="8bd52-116">Will these entities need to be maintained as a single document, or can they be split across multiple documents, tables, collections, and so forth?</span></span>
- <span data-ttu-id="8bd52-117">**规模和结构**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-117">**Scale and structure**.</span></span> <span data-ttu-id="8bd52-118">需要的存储容量总量是多少？</span><span class="sxs-lookup"><span data-stu-id="8bd52-118">What is the overall amount of storage capacity you need?</span></span> <span data-ttu-id="8bd52-119">是否预期对数据进行分区？</span><span class="sxs-lookup"><span data-stu-id="8bd52-119">Do you anticipate partitioning your data?</span></span> 
- <span data-ttu-id="8bd52-120">**数据关系**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-120">**Data relationships**.</span></span> <span data-ttu-id="8bd52-121">数据是否需要支持一对多或多对多关系？</span><span class="sxs-lookup"><span data-stu-id="8bd52-121">Will your data need to support one-to-many or many-to-many relationships?</span></span> <span data-ttu-id="8bd52-122">关系本身是否是数据的重要部分？</span><span class="sxs-lookup"><span data-stu-id="8bd52-122">Are relationships themselves an important part of the data?</span></span> <span data-ttu-id="8bd52-123">是否需要联接或组合来自同一数据集或来自外部数据集的数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-123">Will you need to join or otherwise combine data from within the same dataset, or from external datasets?</span></span> 
- <span data-ttu-id="8bd52-124">**一致性模型**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-124">**Consistency model**.</span></span> <span data-ttu-id="8bd52-125">确保在一个节点中所做更新出现在其他节点中后才能做进一步更改有多重要？</span><span class="sxs-lookup"><span data-stu-id="8bd52-125">How important is it for updates made in one node to appear in other nodes, before further changes can be made?</span></span> <span data-ttu-id="8bd52-126">是否可以接受最终一致性？</span><span class="sxs-lookup"><span data-stu-id="8bd52-126">Can you accept eventual consistency?</span></span> <span data-ttu-id="8bd52-127">是否需要针对事务实现 ACID 保证？</span><span class="sxs-lookup"><span data-stu-id="8bd52-127">Do you need ACID guarantees for transactions?</span></span>
- <span data-ttu-id="8bd52-128">**架构灵活性**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-128">**Schema flexibility**.</span></span> <span data-ttu-id="8bd52-129">将向数据应用什么类型的架构？</span><span class="sxs-lookup"><span data-stu-id="8bd52-129">What kind of schemas will you apply to your data?</span></span> <span data-ttu-id="8bd52-130">将使用固定架构、写入时架构方法还是读取时架构方法？</span><span class="sxs-lookup"><span data-stu-id="8bd52-130">Will you use a fixed schema, a schema-on-write approach, or a schema-on-read approach?</span></span>
- <span data-ttu-id="8bd52-131">**并发**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-131">**Concurrency**.</span></span> <span data-ttu-id="8bd52-132">在更新和同步数据时希望使用什么类型的并发机制？</span><span class="sxs-lookup"><span data-stu-id="8bd52-132">What kind of concurrency mechanism do you want to use when updating and synchronizing data?</span></span> <span data-ttu-id="8bd52-133">应用程序是否将执行可能会冲突的许多更新？</span><span class="sxs-lookup"><span data-stu-id="8bd52-133">Will the application perform many updates that could potentially conflict.</span></span> <span data-ttu-id="8bd52-134">如果是，你可能需要实施记录锁定和悲观并发控制。</span><span class="sxs-lookup"><span data-stu-id="8bd52-134">If so, you may requiring record locking and pessimistic concurrency control.</span></span> <span data-ttu-id="8bd52-135">或者，是否可以支持乐观并发控制？</span><span class="sxs-lookup"><span data-stu-id="8bd52-135">Alternatively, can you support optimistic concurrency controls?</span></span> <span data-ttu-id="8bd52-136">如果是，采用简单的基于时间戳的并发控制已经足够，还是需要附加的多版本并发控制功能？</span><span class="sxs-lookup"><span data-stu-id="8bd52-136">If so, is simple timestamp-based concurrency control enough, or do you need the added functionality of multi-version concurrency control?</span></span>
- <span data-ttu-id="8bd52-137">**数据移动**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-137">**Data movement**.</span></span> <span data-ttu-id="8bd52-138">解决方案是否需要执行 ETL 任务将数据移动到其他存储或数据仓库？</span><span class="sxs-lookup"><span data-stu-id="8bd52-138">Will your solution need to perform ETL tasks to move data to other stores or data warehouses?</span></span>
- <span data-ttu-id="8bd52-139">**数据生命周期**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-139">**Data lifecycle**.</span></span> <span data-ttu-id="8bd52-140">数据是否写入一次读取多次？</span><span class="sxs-lookup"><span data-stu-id="8bd52-140">Is the data write-once, read-many?</span></span> <span data-ttu-id="8bd52-141">是否可以将其移动到冷存储中？</span><span class="sxs-lookup"><span data-stu-id="8bd52-141">Can it be moved into cool or cold storage?</span></span>
- <span data-ttu-id="8bd52-142">**支持的其他功能**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-142">**Other supported features**.</span></span> <span data-ttu-id="8bd52-143">是否需要任何其他特定功能，例如架构验证、聚合、索引、全文搜索、MapReduce 或其他查询功能？</span><span class="sxs-lookup"><span data-stu-id="8bd52-143">Do you need any other specific features, such as schema validation, aggregation, indexing, full-text search, MapReduce, or other query capabilities?</span></span>

### <a name="non-functional-requirements"></a><span data-ttu-id="8bd52-144">非功能性要求</span><span class="sxs-lookup"><span data-stu-id="8bd52-144">Non-functional requirements</span></span>

- <span data-ttu-id="8bd52-145">**性能和可伸缩性**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-145">**Performance and scalability**.</span></span> <span data-ttu-id="8bd52-146">数据性能要求有哪些？</span><span class="sxs-lookup"><span data-stu-id="8bd52-146">What are your data performance requirements?</span></span> <span data-ttu-id="8bd52-147">对数据引入速率和数据处理速率是否有特定要求？</span><span class="sxs-lookup"><span data-stu-id="8bd52-147">Do you have specific requirements for data ingestion rates and data processing rates?</span></span> <span data-ttu-id="8bd52-148">在引入数据后，查询和聚合数据时可接受的响应时间是多少？</span><span class="sxs-lookup"><span data-stu-id="8bd52-148">What are the acceptable response times for querying and aggregation of data once ingested?</span></span> <span data-ttu-id="8bd52-149">需要将数据纵向扩展到多大的规模？</span><span class="sxs-lookup"><span data-stu-id="8bd52-149">How large will you need the data store to scale up?</span></span> <span data-ttu-id="8bd52-150">工作负荷是读取开销更重还是写入开销更重？</span><span class="sxs-lookup"><span data-stu-id="8bd52-150">Is your workload more read-heavy or write-heavy?</span></span>
- <span data-ttu-id="8bd52-151">**可靠性**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-151">**Reliability**.</span></span> <span data-ttu-id="8bd52-152">需要支持什么整体 SLA？</span><span class="sxs-lookup"><span data-stu-id="8bd52-152">What overall SLA do you need to support?</span></span> <span data-ttu-id="8bd52-153">需要为数据使用者提供什么级别的容错？</span><span class="sxs-lookup"><span data-stu-id="8bd52-153">What level of fault-tolerance do you need to provide for data consumers?</span></span> <span data-ttu-id="8bd52-154">需要什么类型的备份和还原功能？</span><span class="sxs-lookup"><span data-stu-id="8bd52-154">What kind of backup and restore capabilities do you need?</span></span> 
- <span data-ttu-id="8bd52-155">**复制**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-155">**Replication**.</span></span> <span data-ttu-id="8bd52-156">数据是否需要分布在多个副本或区域中？</span><span class="sxs-lookup"><span data-stu-id="8bd52-156">Will your data need to be distributed among multiple replicas or regions?</span></span> <span data-ttu-id="8bd52-157">需要什么类型的数据复制功能？</span><span class="sxs-lookup"><span data-stu-id="8bd52-157">What kind of data replication capabilities do you require?</span></span> 
- <span data-ttu-id="8bd52-158">**限制**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-158">**Limits**.</span></span> <span data-ttu-id="8bd52-159">特定数据存储的限制是否可以支持你对规模、连接数和吞吐量的要求？</span><span class="sxs-lookup"><span data-stu-id="8bd52-159">Will the limits of a particular data store support your requirements for scale, number of connections, and throughput?</span></span> 

### <a name="management-and-cost"></a><span data-ttu-id="8bd52-160">管理和成本</span><span class="sxs-lookup"><span data-stu-id="8bd52-160">Management and cost</span></span>

- <span data-ttu-id="8bd52-161">**托管服务**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-161">**Managed service**.</span></span> <span data-ttu-id="8bd52-162">如果可能，请使用托管数据服务，除非你需要只有 IaaS 托管数据存储中才提供的特定功能。</span><span class="sxs-lookup"><span data-stu-id="8bd52-162">When possible, use a managed data service, unless you require specific capabilities that can only be found in an IaaS-hosted data store.</span></span>
- <span data-ttu-id="8bd52-163">**区域可用性**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-163">**Region availability**.</span></span> <span data-ttu-id="8bd52-164">对于托管服务，服务是否在所有 Azure 区域中都可用？</span><span class="sxs-lookup"><span data-stu-id="8bd52-164">For managed services, is the service available in all Azure regions?</span></span> <span data-ttu-id="8bd52-165">解决方案是否需要托管在特定的 Azure 区域中？</span><span class="sxs-lookup"><span data-stu-id="8bd52-165">Does your solution need to be hosted in certain Azure regions?</span></span>
- <span data-ttu-id="8bd52-166">**可移植性**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-166">**Portability**.</span></span> <span data-ttu-id="8bd52-167">需要将数据迁移到本地、外部数据中心还是其他云托管环境？</span><span class="sxs-lookup"><span data-stu-id="8bd52-167">Will your data need to migrated to on-premises, external datacenters, or other cloud hosting environments?</span></span>
- <span data-ttu-id="8bd52-168">**许可**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-168">**Licensing**.</span></span> <span data-ttu-id="8bd52-169">在专有许可证类型与 OSS 许可证类型之间，你是否有偏好？</span><span class="sxs-lookup"><span data-stu-id="8bd52-169">Do you have a preference of a proprietary versus OSS license type?</span></span> <span data-ttu-id="8bd52-170">对于可以使用哪些类型的许可证，是否有任何其他外部限制？</span><span class="sxs-lookup"><span data-stu-id="8bd52-170">Are there any other external restrictions on what type of license you can use?</span></span>
- <span data-ttu-id="8bd52-171">**总体成本**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-171">**Overall cost**.</span></span> <span data-ttu-id="8bd52-172">在你的解决方案内使用此服务的总体成本是多少？</span><span class="sxs-lookup"><span data-stu-id="8bd52-172">What is the overall cost of using the service within your solution?</span></span> <span data-ttu-id="8bd52-173">需要运行多少个实例来支持运行时间和吞吐量要求？</span><span class="sxs-lookup"><span data-stu-id="8bd52-173">How many instances will need to run, to support your uptime and throughput requirements?</span></span> <span data-ttu-id="8bd52-174">在此计算中，请考虑运营成本。</span><span class="sxs-lookup"><span data-stu-id="8bd52-174">Consider operations costs in this calculation.</span></span> <span data-ttu-id="8bd52-175">首选使用托管服务的一个原因是降低了运营成本。</span><span class="sxs-lookup"><span data-stu-id="8bd52-175">One reason to prefer managed services is the reduced operational cost.</span></span>
- <span data-ttu-id="8bd52-176">**成本效益**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-176">**Cost effectiveness**.</span></span> <span data-ttu-id="8bd52-177">是否可以对数据进行分区以便经济高效地存储数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-177">Can you partition your data, to store it more cost effectively?</span></span> <span data-ttu-id="8bd52-178">例如，是否可以将大型对象从昂贵的关系数据库移动到对象存储中？</span><span class="sxs-lookup"><span data-stu-id="8bd52-178">For example, can you move large objects out of an expensive relational database into an object store?</span></span>

### <a name="security"></a><span data-ttu-id="8bd52-179">安全</span><span class="sxs-lookup"><span data-stu-id="8bd52-179">Security</span></span>

- <span data-ttu-id="8bd52-180">**安全性**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-180">**Security**.</span></span> <span data-ttu-id="8bd52-181">需要哪种类型的加密？</span><span class="sxs-lookup"><span data-stu-id="8bd52-181">What type of encryption do you require?</span></span> <span data-ttu-id="8bd52-182">是否需要静态加密？</span><span class="sxs-lookup"><span data-stu-id="8bd52-182">Do you need encryption at rest?</span></span> <span data-ttu-id="8bd52-183">希望使用哪种身份验证机制来连接到数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-183">What authentication mechanism do you want to use to connect to your data?</span></span>
- <span data-ttu-id="8bd52-184">**审核**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-184">**Auditing**.</span></span> <span data-ttu-id="8bd52-185">需要生成哪种类型的审核日志？</span><span class="sxs-lookup"><span data-stu-id="8bd52-185">What kind of audit log do you need to generate?</span></span>
- <span data-ttu-id="8bd52-186">**网络要求**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-186">**Networking requirements**.</span></span> <span data-ttu-id="8bd52-187">是否需要限制或管理从其他网络资源对数据的访问？</span><span class="sxs-lookup"><span data-stu-id="8bd52-187">Do you need to restrict or otherwise manage access to your data from other network resources?</span></span> <span data-ttu-id="8bd52-188">是否要求只能从 Azure 环境内访问数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-188">Does data need to be accessible only from inside the Azure environment?</span></span> <span data-ttu-id="8bd52-189">是否要求可以从特定的 IP 地址或子网访问数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-189">Does the data need to be accessible from specific IP addresses or subnets?</span></span> <span data-ttu-id="8bd52-190">是否要求可以从在本地或其他外部数据中心内托管的应用程序或服务访问数据？</span><span class="sxs-lookup"><span data-stu-id="8bd52-190">Does it need to be accessible from applications or services hosted on-premises or in other external datacenters?</span></span>

### <a name="devops"></a><span data-ttu-id="8bd52-191">DevOps</span><span class="sxs-lookup"><span data-stu-id="8bd52-191">DevOps</span></span>

- <span data-ttu-id="8bd52-192">**技能集**。</span><span class="sxs-lookup"><span data-stu-id="8bd52-192">**Skill set**.</span></span> <span data-ttu-id="8bd52-193">是否有你的团队特别善于使用的特定编程语言、操作系统或其他技术？</span><span class="sxs-lookup"><span data-stu-id="8bd52-193">Are there particular programming languages, operating systems, or other technology that your team is particularly adept at using?</span></span> <span data-ttu-id="8bd52-194">是否有你的团队难以使用的其他技术？</span><span class="sxs-lookup"><span data-stu-id="8bd52-194">Are there others that would be difficult for your team to work with?</span></span>
- <span data-ttu-id="8bd52-195">**客户端** 对于你的开发语言是否有良好的客户端支持？</span><span class="sxs-lookup"><span data-stu-id="8bd52-195">**Clients** Is there good client support for your development languages?</span></span>

<span data-ttu-id="8bd52-196">下面各部分从工作负荷配置文件、数据类型和示例用例等方面对各种数据存储模型进行了比较。</span><span class="sxs-lookup"><span data-stu-id="8bd52-196">The following sections compare various data store models in terms of workload profile, data types, and example use cases.</span></span>

## <a name="relational-database-management-systems-rdbms"></a><span data-ttu-id="8bd52-197">关系数据库管理系统 (RDBMS)</span><span class="sxs-lookup"><span data-stu-id="8bd52-197">Relational database management systems (RDBMS)</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-198">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-198">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-199">新记录的创建和对现有数据的更新都经常发生。</span><span class="sxs-lookup"><span data-stu-id="8bd52-199">Both the creation of new records and updates to existing data happen regularly.</span></span></li>
            <li><span data-ttu-id="8bd52-200">多个操作必须在单个事务中完成。</span><span class="sxs-lookup"><span data-stu-id="8bd52-200">Multiple operations have to be completed in a single transaction.</span></span></li>
            <li><span data-ttu-id="8bd52-201">需要使用聚合函数来执行交叉制表。</span><span class="sxs-lookup"><span data-stu-id="8bd52-201">Requires aggregation functions to perform cross-tabulation.</span></span></li>
            <li><span data-ttu-id="8bd52-202">需要实现与报告工具的强集成。</span><span class="sxs-lookup"><span data-stu-id="8bd52-202">Strong integration with reporting tools is required.</span></span></li>
            <li><span data-ttu-id="8bd52-203">使用数据库约束强制实施关系。</span><span class="sxs-lookup"><span data-stu-id="8bd52-203">Relationships are enforced using database constraints.</span></span></li>
            <li><span data-ttu-id="8bd52-204">使用索引来优化查询性能。</span><span class="sxs-lookup"><span data-stu-id="8bd52-204">Indexes are used to optimize query performance.</span></span></li>
            <li><span data-ttu-id="8bd52-205">允许访问特定的数据子集。</span><span class="sxs-lookup"><span data-stu-id="8bd52-205">Allows access to specific subsets of data.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-206">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-206">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-207">数据是高度规范化的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-207">Data is highly normalized.</span></span></li>
            <li><span data-ttu-id="8bd52-208">数据架构是必需的并强制实施。</span><span class="sxs-lookup"><span data-stu-id="8bd52-208">Database schemas are required and enforced.</span></span></li>
            <li><span data-ttu-id="8bd52-209">数据库中的数据实体之间的多对多关系。</span><span class="sxs-lookup"><span data-stu-id="8bd52-209">Many-to-many relationships between data entities in the database.</span></span></li>
            <li><span data-ttu-id="8bd52-210">约束是在架构中定义的，并施加于数据库中的任何数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-210">Constraints are defined in the schema and imposed on any data in the database.</span></span></li>
            <li><span data-ttu-id="8bd52-211">数据需要具有高完整性。</span><span class="sxs-lookup"><span data-stu-id="8bd52-211">Data requires high integrity.</span></span> <span data-ttu-id="8bd52-212">索引和关系需要准确地维护。</span><span class="sxs-lookup"><span data-stu-id="8bd52-212">Indexes and relationships need to be maintained accurately.</span></span></li>
            <li><span data-ttu-id="8bd52-213">数据需要具有强一致性。</span><span class="sxs-lookup"><span data-stu-id="8bd52-213">Data requires strong consistency.</span></span> <span data-ttu-id="8bd52-214">事务的运行方式将确保所有数据对于所有用户和进程而言都 100% 一致。</span><span class="sxs-lookup"><span data-stu-id="8bd52-214">Transactions operate in a way that ensures all data are 100% consistent for all users and processes.</span></span></li>
            <li><span data-ttu-id="8bd52-215">各个数据条目的大小预计为中小型的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-215">Size of individual data entries is intended to be small to medium-sized.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-216">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-216">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-217">业务线（人力资本管理、客户关系管理、企业资源规划）</span><span class="sxs-lookup"><span data-stu-id="8bd52-217">Line of business  (human capital management, customer relationship management, enterprise resource planning)</span></span></li>
            <li><span data-ttu-id="8bd52-218">库存管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-218">Inventory management</span></span></li>
            <li><span data-ttu-id="8bd52-219">报告数据库</span><span class="sxs-lookup"><span data-stu-id="8bd52-219">Reporting database</span></span></li>
            <li><span data-ttu-id="8bd52-220">计帐</span><span class="sxs-lookup"><span data-stu-id="8bd52-220">Accounting</span></span></li>
            <li><span data-ttu-id="8bd52-221">资产管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-221">Asset management</span></span></li>
            <li><span data-ttu-id="8bd52-222">基金管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-222">Fund management</span></span></li>
            <li><span data-ttu-id="8bd52-223">订单管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-223">Order management</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="document-databases"></a><span data-ttu-id="8bd52-224">文档数据库</span><span class="sxs-lookup"><span data-stu-id="8bd52-224">Document databases</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-225">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-225">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-226">常规用途。</span><span class="sxs-lookup"><span data-stu-id="8bd52-226">General purpose.</span></span></li>
            <li><span data-ttu-id="8bd52-227">插入和更新操作很常见。</span><span class="sxs-lookup"><span data-stu-id="8bd52-227">Insert and update operations are common.</span></span> <span data-ttu-id="8bd52-228">新记录的创建和对现有数据的更新都经常发生。</span><span class="sxs-lookup"><span data-stu-id="8bd52-228">Both the creation of new records and updates to existing data happen regularly.</span></span></li>
            <li><span data-ttu-id="8bd52-229">没有对象关系阻抗不匹配。</span><span class="sxs-lookup"><span data-stu-id="8bd52-229">No object-relational impedance mismatch.</span></span> <span data-ttu-id="8bd52-230">文档可以更好地匹配应用程序代码中使用的对象结构。</span><span class="sxs-lookup"><span data-stu-id="8bd52-230">Documents can better match the object structures used in application code.</span></span></li>
            <li><span data-ttu-id="8bd52-231">更常使用乐观并发。</span><span class="sxs-lookup"><span data-stu-id="8bd52-231">Optimistic concurrency is more commonly used.</span></span></li>
            <li><span data-ttu-id="8bd52-232">使用方应用程序必须修改和处理数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-232">Data must be modified and processed by consuming application.</span></span></li>
            <li><span data-ttu-id="8bd52-233">数据需要基于多个字段编制索引。</span><span class="sxs-lookup"><span data-stu-id="8bd52-233">Data requires index on multiple fields.</span></span></li>
            <li><span data-ttu-id="8bd52-234">单个文档将作为单个块进行检索和写入。</span><span class="sxs-lookup"><span data-stu-id="8bd52-234">Individual documents are retrieved and written as a single block.</span></span></li>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-235">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-235">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-236">可以采用非规范化的方式管理数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-236">Data can be managed in de-normalized way.</span></span></li>
            <li><span data-ttu-id="8bd52-237">单个文档的数据大小相对较小。</span><span class="sxs-lookup"><span data-stu-id="8bd52-237">Size of individual document data is relatively small.</span></span></li>
            <li><span data-ttu-id="8bd52-238">每个文档类型可以使用其自己的架构。</span><span class="sxs-lookup"><span data-stu-id="8bd52-238">Each document type can use its own schema.</span></span></li>
            <li><span data-ttu-id="8bd52-239">文档可以包括可选字段。</span><span class="sxs-lookup"><span data-stu-id="8bd52-239">Documents can include optional fields.</span></span></li>
            <li><span data-ttu-id="8bd52-240">文档数据是半结构化的，这意味着每个字段的数据类型不是严格定义的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-240">Document data is semi-structured, meaning that data types of each field are not strictly defined.</span></span></li>
            <li><span data-ttu-id="8bd52-241">支持数据聚合。</span><span class="sxs-lookup"><span data-stu-id="8bd52-241">Data aggregation is supported.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-242">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-242">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-243">产品目录</span><span class="sxs-lookup"><span data-stu-id="8bd52-243">Product catalog</span></span></li>
            <li><span data-ttu-id="8bd52-244">用户帐户</span><span class="sxs-lookup"><span data-stu-id="8bd52-244">User accounts</span></span></li>
            <li><span data-ttu-id="8bd52-245">材料清单</span><span class="sxs-lookup"><span data-stu-id="8bd52-245">Bill of materials</span></span></li>
            <li><span data-ttu-id="8bd52-246">个性化</span><span class="sxs-lookup"><span data-stu-id="8bd52-246">Personalization</span></span></li>
            <li><span data-ttu-id="8bd52-247">内容管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-247">Content management</span></span></li>
            <li><span data-ttu-id="8bd52-248">运营数据</span><span class="sxs-lookup"><span data-stu-id="8bd52-248">Operations data</span></span></li>
            <li><span data-ttu-id="8bd52-249">库存管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-249">Inventory management</span></span></li>
            <li><span data-ttu-id="8bd52-250">事务历史记录数据</span><span class="sxs-lookup"><span data-stu-id="8bd52-250">Transaction history data</span></span></li>
            <li><span data-ttu-id="8bd52-251">其他 NoSQL 存储的具体化视图。</span><span class="sxs-lookup"><span data-stu-id="8bd52-251">Materialized view of other NoSQL stores.</span></span> <span data-ttu-id="8bd52-252">替换文件/BLOB 索引。</span><span class="sxs-lookup"><span data-stu-id="8bd52-252">Replaces file/BLOB indexing.</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="keyvalue-stores"></a><span data-ttu-id="8bd52-253">键/值存储</span><span class="sxs-lookup"><span data-stu-id="8bd52-253">Key/value stores</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-254">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-254">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-255">将使用单个 ID 键（例如字典）标识和访问数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-255">Data is identified and accessed using a single ID key, like a dictionary.</span></span></li>
            <li><span data-ttu-id="8bd52-256">高度可伸缩。</span><span class="sxs-lookup"><span data-stu-id="8bd52-256">Massively scalable.</span></span></li>
            <li><span data-ttu-id="8bd52-257">不需要使用联接、锁定或联合。</span><span class="sxs-lookup"><span data-stu-id="8bd52-257">No joins, lock, or unions are required.</span></span></li>
            <li><span data-ttu-id="8bd52-258">不使用聚合机制。</span><span class="sxs-lookup"><span data-stu-id="8bd52-258">No aggregation mechanisms are used.</span></span></li>
            <li><span data-ttu-id="8bd52-259">通常不使用辅助索引。</span><span class="sxs-lookup"><span data-stu-id="8bd52-259">Secondary indexes are generally not used.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-260">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-260">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-261">数据大小通常很大。</span><span class="sxs-lookup"><span data-stu-id="8bd52-261">Data size tends to be large.</span></span></li>
            <li><span data-ttu-id="8bd52-262">每个键都与单个值相关联，该值是一个非托管数据 BLOB。</span><span class="sxs-lookup"><span data-stu-id="8bd52-262">Each key is associated with a single value, which is an unmanaged data BLOB.</span></span></li>
            <li><span data-ttu-id="8bd52-263">未实施架构。</span><span class="sxs-lookup"><span data-stu-id="8bd52-263">There is no schema enforcement.</span></span></li>
            <li><span data-ttu-id="8bd52-264">实体之间没有关系。</span><span class="sxs-lookup"><span data-stu-id="8bd52-264">No relationships between entities.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-265">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-265">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-266">数据缓存</span><span class="sxs-lookup"><span data-stu-id="8bd52-266">Data caching</span></span></li>
            <li><span data-ttu-id="8bd52-267">会话管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-267">Session management</span></span></li>
            <li><span data-ttu-id="8bd52-268">用户首选项和配置文件管理</span><span class="sxs-lookup"><span data-stu-id="8bd52-268">User preference and profile management</span></span></li>
            <li><span data-ttu-id="8bd52-269">产品推荐和广告服务</span><span class="sxs-lookup"><span data-stu-id="8bd52-269">Product recommendation and ad serving</span></span></li>
            <li><span data-ttu-id="8bd52-270">字典</span><span class="sxs-lookup"><span data-stu-id="8bd52-270">Dictionaries</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="graph-databases"></a><span data-ttu-id="8bd52-271">图形数据库</span><span class="sxs-lookup"><span data-stu-id="8bd52-271">Graph databases</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-272">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-272">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-273">数据项之间的关系非常复杂，涉及相关数据项之间的许多跃点。</span><span class="sxs-lookup"><span data-stu-id="8bd52-273">The relationships between data items are very complex, involving many hops between related data items.</span></span></li>
            <li><span data-ttu-id="8bd52-274">数据项之间的关系是动态的并且随时间变化。</span><span class="sxs-lookup"><span data-stu-id="8bd52-274">The relationship between data items are dynamic and change over time.</span></span></li>
            <li><span data-ttu-id="8bd52-275">对象之间的关系是头等关系，不需要使用外键和联接进行遍历。</span><span class="sxs-lookup"><span data-stu-id="8bd52-275">Relationships between objects are first-class citizens, without requiring foreign-keys and joins to traverse.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-276">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-276">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-277">数据由节点和关系组成。</span><span class="sxs-lookup"><span data-stu-id="8bd52-277">Data is comprised of nodes and relationships.</span></span></li>
            <li><span data-ttu-id="8bd52-278">节点类似于表行或 JSON 文档。</span><span class="sxs-lookup"><span data-stu-id="8bd52-278">Nodes are similar to table rows or JSON documents.</span></span></li>
            <li><span data-ttu-id="8bd52-279">关系与节点同等重要，并且是直接以查询语言公开的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-279">Relationships are just as important as nodes, and are exposed directly in the query language.</span></span></li>
            <li><span data-ttu-id="8bd52-280">复合对象（例如具有多个电话号码的人员）通常分解为多个单独的较小节点，这些节点通过可遍历的关系组合在一起</span><span class="sxs-lookup"><span data-stu-id="8bd52-280">Composite objects, such as a person with multiple phone numbers, tend to be broken into separate, smaller nodes, combined with traversable relationships</span></span> </li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-281">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-281">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-282">组织结构图</span><span class="sxs-lookup"><span data-stu-id="8bd52-282">Organization charts</span></span></li>
            <li><span data-ttu-id="8bd52-283">社交关系图</span><span class="sxs-lookup"><span data-stu-id="8bd52-283">Social graphs</span></span></li>
            <li><span data-ttu-id="8bd52-284">欺诈检测</span><span class="sxs-lookup"><span data-stu-id="8bd52-284">Fraud detection</span></span></li>
            <li><span data-ttu-id="8bd52-285">分析</span><span class="sxs-lookup"><span data-stu-id="8bd52-285">Analytics</span></span></li>
            <li><span data-ttu-id="8bd52-286">推荐引擎</span><span class="sxs-lookup"><span data-stu-id="8bd52-286">Recommendation engines</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="column-family-databases"></a><span data-ttu-id="8bd52-287">列系列数据库</span><span class="sxs-lookup"><span data-stu-id="8bd52-287">Column-family databases</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-288">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-288">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-289">大多数列系列数据库都极快地执行写入操作。</span><span class="sxs-lookup"><span data-stu-id="8bd52-289">Most column-family databases perform write operations extremely quickly.</span></span></li>
            <li><span data-ttu-id="8bd52-290">更新和删除操作很少发生。</span><span class="sxs-lookup"><span data-stu-id="8bd52-290">Update and delete operations are rare.</span></span></li>
            <li><span data-ttu-id="8bd52-291">设计用于提供高吞吐量低延迟访问。</span><span class="sxs-lookup"><span data-stu-id="8bd52-291">Designed to provide high throughput and low-latency access.</span></span></li>
            <li><span data-ttu-id="8bd52-292">支持轻松以查询方式访问非常大的记录中的一组特定字段。</span><span class="sxs-lookup"><span data-stu-id="8bd52-292">Supports easy query access to a particular set of fields within a much larger record.</span></span></li>
            <li><span data-ttu-id="8bd52-293">高度可伸缩。</span><span class="sxs-lookup"><span data-stu-id="8bd52-293">Massively scalable.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-294">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-294">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-295">数据存储在由一个键列和一个或多个列系列组成的表中。</span><span class="sxs-lookup"><span data-stu-id="8bd52-295">Data is stored in tables consisting of a key column and one or more column families.</span></span></li>
            <li><span data-ttu-id="8bd52-296">具体的列可能因各个行而异。</span><span class="sxs-lookup"><span data-stu-id="8bd52-296">Specific columns can vary by individual rows.</span></span></li>
            <li><span data-ttu-id="8bd52-297">可以通过 get 和 put 命令访问各个单元格</span><span class="sxs-lookup"><span data-stu-id="8bd52-297">Individual cells are accessed via get and put commands</span></span></li>
            <li><span data-ttu-id="8bd52-298">使用扫描命令返回多个行。</span><span class="sxs-lookup"><span data-stu-id="8bd52-298">Multiple rows are returned using a scan command.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-299">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-299">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-300">建议</span><span class="sxs-lookup"><span data-stu-id="8bd52-300">Recommendations</span></span></li>
            <li><span data-ttu-id="8bd52-301">个性化</span><span class="sxs-lookup"><span data-stu-id="8bd52-301">Personalization</span></span></li>
            <li><span data-ttu-id="8bd52-302">传感器数据</span><span class="sxs-lookup"><span data-stu-id="8bd52-302">Sensor data</span></span></li>
            <li><span data-ttu-id="8bd52-303">遥测</span><span class="sxs-lookup"><span data-stu-id="8bd52-303">Telemetry</span></span></li>
            <li><span data-ttu-id="8bd52-304">消息传递</span><span class="sxs-lookup"><span data-stu-id="8bd52-304">Messaging</span></span></li>
            <li><span data-ttu-id="8bd52-305">社交媒体分析</span><span class="sxs-lookup"><span data-stu-id="8bd52-305">Social media analytics</span></span></li>
            <li><span data-ttu-id="8bd52-306">Web analytics</span><span class="sxs-lookup"><span data-stu-id="8bd52-306">Web analytics</span></span></li>
            <li><span data-ttu-id="8bd52-307">活动监视</span><span class="sxs-lookup"><span data-stu-id="8bd52-307">Activity monitoring</span></span></li>
            <li><span data-ttu-id="8bd52-308">天气和其他时序数据</span><span class="sxs-lookup"><span data-stu-id="8bd52-308">Weather and other time-series data</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="search-engine-databases"></a><span data-ttu-id="8bd52-309">搜索引擎数据库</span><span class="sxs-lookup"><span data-stu-id="8bd52-309">Search engine databases</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-310">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-310">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-311">为来自多个源和服务的数据编制索引。</span><span class="sxs-lookup"><span data-stu-id="8bd52-311">Indexing data from multiple sources and services.</span></span></li>
            <li><span data-ttu-id="8bd52-312">查询是即席的，可能会很复杂。</span><span class="sxs-lookup"><span data-stu-id="8bd52-312">Queries are ad-hoc and can be complex.</span></span></li>
            <li><span data-ttu-id="8bd52-313">需要聚合。</span><span class="sxs-lookup"><span data-stu-id="8bd52-313">Requires aggregation.</span></span></li>
            <li><span data-ttu-id="8bd52-314">全文搜索是必需的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-314">Full text search is required.</span></span></li>
            <li><span data-ttu-id="8bd52-315">即席自助查询是必需的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-315">Ad hoc self-service query is required.</span></span></li>
            <li><span data-ttu-id="8bd52-316">需要通过所有字段的索引进行数据分析。</span><span class="sxs-lookup"><span data-stu-id="8bd52-316">Data analysis with index on all fields is required.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-317">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-317">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-318">半结构化的或非结构化的</span><span class="sxs-lookup"><span data-stu-id="8bd52-318">Semi-structured or unstructured</span></span></li>
            <li><span data-ttu-id="8bd52-319">文本</span><span class="sxs-lookup"><span data-stu-id="8bd52-319">Text</span></span></li>
            <li><span data-ttu-id="8bd52-320">其中引用了结构化数据的文本</span><span class="sxs-lookup"><span data-stu-id="8bd52-320">Text with reference to structured data</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-321">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-321">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-322">产品目录</span><span class="sxs-lookup"><span data-stu-id="8bd52-322">Product catalogs</span></span></li>
            <li><span data-ttu-id="8bd52-323">站点搜索</span><span class="sxs-lookup"><span data-stu-id="8bd52-323">Site search</span></span></li>
            <li><span data-ttu-id="8bd52-324">日志记录</span><span class="sxs-lookup"><span data-stu-id="8bd52-324">Logging</span></span></li>
            <li><span data-ttu-id="8bd52-325">分析</span><span class="sxs-lookup"><span data-stu-id="8bd52-325">Analytics</span></span></li>
            <li><span data-ttu-id="8bd52-326">购物网站</span><span class="sxs-lookup"><span data-stu-id="8bd52-326">Shopping sites</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="data-warehouse"></a><span data-ttu-id="8bd52-327">数据仓库</span><span class="sxs-lookup"><span data-stu-id="8bd52-327">Data warehouse</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-328">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-328">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-329">数据分析</span><span class="sxs-lookup"><span data-stu-id="8bd52-329">Data analytics</span></span></li>
            <li><span data-ttu-id="8bd52-330">企业 BI</span><span class="sxs-lookup"><span data-stu-id="8bd52-330">Enterprise BI</span></span>   </li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-331">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-331">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-332">来自多个源的历史数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-332">Historical data from multiple sources.</span></span></li>
            <li><span data-ttu-id="8bd52-333">通常是非规范化的，采用“星型”或“雪花型”架构，包含事实数据表和维度表。</span><span class="sxs-lookup"><span data-stu-id="8bd52-333">Usually denormalized in a "star" or "snowflake" schema, consisting of fact and dimension tables.</span></span></li>
            <li><span data-ttu-id="8bd52-334">通常按计划定期加载新数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-334">Usually loaded with new data on a scheduled basis.</span></span></li>
            <li><span data-ttu-id="8bd52-335">维度表通常包括实体的多个历史版本，称为*渐变维度*。</span><span class="sxs-lookup"><span data-stu-id="8bd52-335">Dimension tables often include multiple historic versions of an entity, referred to as a *slowly changing dimension*.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-336">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-336">**Examples**</span></span></td>
    <td><span data-ttu-id="8bd52-337">为分析模型、报表和仪表板提供数据的企业数据仓库。</span><span class="sxs-lookup"><span data-stu-id="8bd52-337">An enterprise data warehouse that provides data for analytical models, reports, and dashboards.</span></span>
    </td>
</tr>
</table>


## <a name="time-series-databases"></a><span data-ttu-id="8bd52-338">时序数据库</span><span class="sxs-lookup"><span data-stu-id="8bd52-338">Time series databases</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-339">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-339">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-340">绝大部分 (95-99%) 操作是写入。</span><span class="sxs-lookup"><span data-stu-id="8bd52-340">An overwhelmingly proportion of operations (95-99%) are writes.</span></span></li>
            <li><span data-ttu-id="8bd52-341">记录通常按时间顺序依次追加。</span><span class="sxs-lookup"><span data-stu-id="8bd52-341">Records are generally appended sequentially in time order.</span></span></li>
            <li><span data-ttu-id="8bd52-342">很少进行更新。</span><span class="sxs-lookup"><span data-stu-id="8bd52-342">Updates are rare.</span></span></li>
            <li><span data-ttu-id="8bd52-343">删除批量进行，并且针对连续的块或记录执行。</span><span class="sxs-lookup"><span data-stu-id="8bd52-343">Deletes occur in bulk, and are made to contiguous blocks or records.</span></span></li>
            <li><span data-ttu-id="8bd52-344">读取请求可能会大于可用内存。</span><span class="sxs-lookup"><span data-stu-id="8bd52-344">Read requests can be larger than available memory.</span></span></li>
            <li><span data-ttu-id="8bd52-345">通常会有多个读取同时发生。</span><span class="sxs-lookup"><span data-stu-id="8bd52-345">It's common for multiple reads to occur simultaneously.</span></span></li>
            <li><span data-ttu-id="8bd52-346">数据按升序或降序时间顺序依次读取。</span><span class="sxs-lookup"><span data-stu-id="8bd52-346">Data is read sequentially in either ascending or descending time order.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-347">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-347">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-348">一个用作主键和排序机制的时间戳。</span><span class="sxs-lookup"><span data-stu-id="8bd52-348">A time stamp that is used as the primary key and sorting mechanism.</span></span></li>
            <li><span data-ttu-id="8bd52-349">来自条目的度量或者对条目所代表的内容的描述。</span><span class="sxs-lookup"><span data-stu-id="8bd52-349">Measurements from the entry or descriptions of what the entry represents.</span></span></li>
            <li><span data-ttu-id="8bd52-350">相关标记，用于定义关于条目的类型、来源和其他信息的附加信息。</span><span class="sxs-lookup"><span data-stu-id="8bd52-350">Tags that define additional information about the type, origin, and other information about the entry.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-351">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-351">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-352">监视和事件遥测。</span><span class="sxs-lookup"><span data-stu-id="8bd52-352">Monitoring and event telemetry.</span></span></li>
            <li><span data-ttu-id="8bd52-353">传感器或其他 IoT 数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-353">Sensor or other IoT data.</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="object-storage"></a><span data-ttu-id="8bd52-354">对象存储</span><span class="sxs-lookup"><span data-stu-id="8bd52-354">Object storage</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-355">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-355">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-356">由键进行标识。</span><span class="sxs-lookup"><span data-stu-id="8bd52-356">Identified by key.</span></span></li>
            <li><span data-ttu-id="8bd52-357">对象可能可以公开访问，也可能只能以私有方式访问。</span><span class="sxs-lookup"><span data-stu-id="8bd52-357">Objects may be publicly or privately accessible.</span></span></li>
            <li><span data-ttu-id="8bd52-358">内容通常是诸如电子表格、图像或视频文件的资产。</span><span class="sxs-lookup"><span data-stu-id="8bd52-358">Content is typically an asset such as a spreadsheet, image, or video file.</span></span></li>
            <li><span data-ttu-id="8bd52-359">内容必须是持久性的（永久性的），并且位于任何应用程序层或虚拟机的外部。</span><span class="sxs-lookup"><span data-stu-id="8bd52-359">Content must be durable (persistent), and external to any application tier or virtual machine.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-360">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-360">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-361">数据大小较大。</span><span class="sxs-lookup"><span data-stu-id="8bd52-361">Data size is large.</span></span></li>
            <li><span data-ttu-id="8bd52-362">Blob 数据。</span><span class="sxs-lookup"><span data-stu-id="8bd52-362">Blob data.</span></span></li>
            <li><span data-ttu-id="8bd52-363">值是不透明的。</span><span class="sxs-lookup"><span data-stu-id="8bd52-363">Value is opaque.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-364">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-364">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-365">图像、视频、Office 文档、PDF</span><span class="sxs-lookup"><span data-stu-id="8bd52-365">Images, videos, office documents, PDFs</span></span></li>
            <li><span data-ttu-id="8bd52-366">CSS、脚本、CSV</span><span class="sxs-lookup"><span data-stu-id="8bd52-366">CSS, Scripts, CSV</span></span></li>
            <li><span data-ttu-id="8bd52-367">静态 HTML、JSON</span><span class="sxs-lookup"><span data-stu-id="8bd52-367">Static HTML, JSON</span></span></li>
            <li><span data-ttu-id="8bd52-368">日志和审核文件</span><span class="sxs-lookup"><span data-stu-id="8bd52-368">Log and audit files</span></span></li>
            <li><span data-ttu-id="8bd52-369">数据库备份</span><span class="sxs-lookup"><span data-stu-id="8bd52-369">Database backups</span></span></li>
        </ul>
    </td>
</tr>
</table>

## <a name="shared-files"></a><span data-ttu-id="8bd52-370">共享文件</span><span class="sxs-lookup"><span data-stu-id="8bd52-370">Shared files</span></span>

<table>
<tr><td><span data-ttu-id="8bd52-371">**工作负荷**</span><span class="sxs-lookup"><span data-stu-id="8bd52-371">**Workload**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-372">从与文件系统进行交互的现有应用进行迁移。</span><span class="sxs-lookup"><span data-stu-id="8bd52-372">Migration from existing apps that interact with the file system.</span></span></li>
            <li><span data-ttu-id="8bd52-373">需要 SMB 接口。</span><span class="sxs-lookup"><span data-stu-id="8bd52-373">Requires SMB interface.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-374">**数据类型**</span><span class="sxs-lookup"><span data-stu-id="8bd52-374">**Data type**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-375">一组分层文件夹中的文件。</span><span class="sxs-lookup"><span data-stu-id="8bd52-375">Files in a hierarchical set of folders.</span></span></li>
            <li><span data-ttu-id="8bd52-376">可以通过标准 I/O 库进行访问。</span><span class="sxs-lookup"><span data-stu-id="8bd52-376">Accessible with standard I/O libraries.</span></span></li>
        </ul>
    </td>
</tr>
<tr><td><span data-ttu-id="8bd52-377">**示例**</span><span class="sxs-lookup"><span data-stu-id="8bd52-377">**Examples**</span></span></td>
    <td>
        <ul>
            <li><span data-ttu-id="8bd52-378">旧式文件</span><span class="sxs-lookup"><span data-stu-id="8bd52-378">Legacy files</span></span></li>
            <li><span data-ttu-id="8bd52-379">可以从许多 VM 或应用实例访问的共享内容</span><span class="sxs-lookup"><span data-stu-id="8bd52-379">Shared content accessible among a number of VMs or app instances</span></span></li>
        </ul>
    </td>
</tr>
</table>