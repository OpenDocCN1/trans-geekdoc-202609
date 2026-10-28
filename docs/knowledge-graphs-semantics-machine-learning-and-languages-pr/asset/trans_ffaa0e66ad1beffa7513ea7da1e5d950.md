
```sparql
SELECT DISTINCT ?Provider ?Name ?Web WHERE {
  ?Provider a :DataCooperative .
  ?Provider dpv:hasName ?Name .
  ?Provider dcat:landingPage ?Web . }
```

**列表4：** 检索数据合作社的SPARQL查询。

```turtle
ex:altruism_logs a :RegisterOfDataAltruismActivity ;
  dct:description "Activity logs of the Data Altruism Organisation A" ;
  dct:created "2023-11-04"^^xsd:date ;
  dct:modified "2023-11-13"^^xsd:date ;
  dct:publisher ex:altruism_A ; dcat:record ex:log_001 .
ex:altruism_A a :DataAltruismOrganisation ;
  dpv:hasName "Data Altruism Organisation A" ;
  dpv:hasAddress "Lisboa, Portugal" ;
  dcat:landingPage <http://example.com/altruism_A> .
ex:log_001 a dcat:CatalogRecord ;
  dct:created "2023-11-13"^^xsd:date ;
  :hasDataUser ex:userZ ; :hasFee "1000€"^^xsd:string ;
  dpv:hasPersonalDataHandling [
    dct:description "Download and reuse anonymised health records to improve healthcare" ;
    dpv:hasProcessing :Download, :Reuse ; dpv:hasDuration 6226453 ;
    dpv:hasPurpose :DataAltruism, :ImproveHealthcare ;
    dpv:hasPersonalData dpv-pd:HealthRecord ;
    dpv:hasTechnicalMeasure dpv:Anonymisation ] .
ex:userZ a :DataUser ; dpv:hasName "Data User Z" ;
  dpv:hasContact "mailto:user_z@email.com" .
```

**列表5：** 数据利他活动日志登记册示例。

分别指数据中介机构和利他组织。通过使用所识别和开发的语义词汇表将公共登记册存储在 RDF 中，此类登记册可以很容易地使用诸如 SPARQL 之类的查询语言进行查询，从而自动检索有关数据中介服务提供商的信息。列表4提供了一个数据合作社查询示例，该查询将返回提供数据合作社服务的数据中介服务提供商列表，包括其名称和公共网站。

列表5提供了一个数据利他活动登记册的示例，通过新创建的概念 RegisterOfDataAltruismActivity 表示。活动日志应与使用数据的实体相关联，并可使用 DPV 的 hasPersonalDataHandling 进行记录，以提供有关数据处理的信息，包括处理时长、目的和（个人）数据类别。

```turtle
ex:consentForm_001 a :EuropeanDataAltruismConsentForm ;
  dpv:hasIdentifier <http://example.com/consentForm_001> ;
  dpv:hasDataSubject ex:Anne ; dpv:isIndicatedBy ex:Anne ;
  dpv:isIndicatedAtTime "2022-12-14" ;
  dpv:hasPersonalDataHandling [
    dpv:hasPurpose :DataAltruism , :ImproveTransportMobility ;
    dpv:hasLegalBasis dpv-gdpr:A6-1-a ;
    dpv:hasPersonalData dpv-pd:Location ;
    dpv:hasProcessing dpv:Use , dpv:Store ;
    dpv:hasDataController [
      a dpv:DataController , :DataAltruismOrganisation ;
      dpv:hasName "Company A" ] ] .
```

**列表6：** 数据利他同意书，其中数据主体 Anne 同意将其位置数据用于改善交通出行的利他目的。

### 4.3. 统一、机器可读的数据利他表格

正如前两个小节中的示例所证明的，所识别的词汇表以及我们自己开发的词汇表，也可以用于自动化生成面向数据主体的同意书和面向数据持有者的许可表。通过在设计上依靠这些技术，欧洲数据利他表格将促进互操作性，并可在整个欧盟范围内重复使用。列表6提供了一个数据主体使用术语 EuropeanDataAltruismConsentForm 的同意书示例。在此示例中，我们使用了词汇表中定义的利他处理目的。因此，我们将 DataAltruism 定义为 dpv:Purpose 的子类，并指定了七个可用于数据利他场景的新目的：ImproveHealthcare、CombatClimateChange、ImproveTransportMobility（用于列表6）、ProvideOfficialStatistics、ImprovePublicServices、ScientificResearch 和 PublicPolicyMaking。DGA 中提到的其他目的也包含在专门词汇表中。类似地，列表7中我们提供了一个数据持有者许可表的示例。

```turtle
ex:permissionForm_001 a dpv:Permission ;
    dpv:hasIdentifier <http://example.com/permissionForm_001> ;
    :hasDataHolder ex:dataHolderA ; dpv:isIndicatedBy ex:dataHolderA ;
    dpv:isIndicatedAtTime "2022-12-15" ;
    dpv:hasPersonalDataHandling [
        dpv:hasPurpose :DataAltruism, :ProvideOfficialStatistics ;
        dpv:hasLegalBasis :A2-6 ; dpv:hasData dpv:AnonymisedData ;
        dpv:hasProcessing dpv:Use, dpv:Store ;
        dpv:hasDataController [
            a dpv:DataController, :DataAltruismOrganisation ;
            dpv:hasName "Company A" ] ] .
```

**列表7：** 数据利他许可，其中数据持有者 A 允许将其匿名数据用于提供官方统计数据的利他目的。

## 5. 讨论

所有已定义术语的完整列表可在 https://w3id.org/dgaterms 获取，采用开放且许可宽松的许可证。关于如何使用语义技术来实施 DGA 的分析产生了一些有前景的应用，但也可以识别出一些障碍。在优势方面，以下几点应特别注意：

- 语义技术有助于在法规条款上形成共识。
- 机器可读策略可以有效地用 RDF 表示，并用适当的推理机执行。
- 对数据利他同意表达进行认证的信任技术可提供法律确定性，并鼓励数据重用，这完全符合 DGA 的精神。
- 语义网技术擅长在 Web 上发布策略，JSON-LD 序列化可被 Web 开发人员轻松使用。此外，RDF 可以有效地充当未来表达语言之间的桥梁。
- 数据利他行为可以以非经济形式得到回报，从而反过来鼓励进一步的数据共享。

然而，可以识别出以下局限性：

- 策略中声明的大多数条件将无法自动执行，而且策略的声明性本质将不可避免地导致数据滥用。
- 如果没有任何本体获得主导性传播，未得到公共当局的认可，或者严重分歧妨碍达成共识，那么协议可能无法达成。

## 6. 结论与未来工作

尽管欧洲数据战略十分强大，但若要实现个人、公司和政府之间共享数据的公共空间，仍需克服许多互操作性挑战。因此，本工作对 DGA 的要求进行了分析，并提供了一个通用语义模型来记录公共部门机构、数据中介服务提供商和利他组织的活动，这是攻克这一互操作性挑战的第一步。按照我们的提议，我们识别了为 DGA 带来的新型数据共享实体建模所需的利益相关方、信息和需求，并提供了一个语义词汇表及其使用示例，可用于自动化这些新实体的文档编制任务。至于未来工作，应探索《数据法案》和“数据空间”提案，以提高本工作质量，并促进欧洲共同数据空间所设想的互操作性。

## 致谢

这项工作部分得到了项目 Knowledge Spaces: Técnicas y herramientas para la gestión de grafos de conocimientos para dar soporte a espacios de datos（授权号 PID2020-118274RB-I00，由 MCIN/AEI/10.13039/501100011033 资助）的资助。本研究还得到了欧盟地平线2020研究与创新计划下 Marie Skłodowska-Curie 资助协议 No 813497 (PROTECT) 的支持，以及由爱尔兰科学基金会资助、并通过授权号 #13/RC/2106_P2 在欧洲区域发展基金（ERDF）下共同资助的 ADAPT SFI 研究中心的资助。

*这是一项正在进行的工作，已作为提案提交给数据隐私词汇与控制社区组（DPVCG），以将 DGA 整合到其输出中。*

## 参考文献

- [1] 欧洲议会和理事会2016年4月27日关于在个人数据处理方面保护自然人以及此类数据自由流动的第2016/679号条例（欧盟），并废除指令95/46/EC（《通用数据保护条例》）；2018年。可从以下网址获取：https://eur-lex.europa.eu/eli/reg/2016/679/oj。
- [2] 欧盟委员会向欧洲议会、理事会、欧洲经济与社会委员会和地区委员会提交的通报——欧洲数据战略；2020年。可从以下网址获取：https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A52020DC0066。
- [3] 欧洲议会和理事会2022年5月30日关于欧洲数据治理并修订第(EU)2018/1724号条例的(EU)2022/868号条例（《数据治理法》）；2022年。可从以下网址获取：http://data.europa.eu/eli/reg/2022/868/oj/eng。
- [4] 欧洲议会和理事会关于欧洲健康数据空间的条例提案；2022年。可从以下网址获取：https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A52022PC0197。
- [5] 欧洲议会和理事会关于公平获取和使用数据的统一规则的条例提案（《数据法案》）；2022年。可从以下网址获取：https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=COM%3A2022%3A68%3AFIN。
- [6] de Oliveira Rodrigues CM, de Freitas FLG, Barreiros EFS, de Azevedo RR, de Almeida Filho AT. 法律本体随时间演变：系统映射研究. Expert Systems with Applications. 2019;130:12-30.
- [7] Esteves B, Rodríguez-Doncel V. 表示GDPR中信息流的本体与策略语言分析. Semantic Web Journal. 2022.
- [8] Iannella R, Villata S. ODRL信息模型2.2. W3C推荐标准. 2018.
- [9] Parducci B, Lockhart H, Rissanen E. 可扩展访问控制标记语言（XACML）3.0版 [OASIS标准]；2013. 可从以下网址获取：http://docs.oasis-open.org/xacml/3.0/xacml-3.0-core-spec-os-en.html。
- [10] Palmirani M, Governatori G, Athan T, Boley H, Paschke A, Wyner A. LegalRuleML核心规范1.0版；2021. 可从以下网址获取：https://docs.oasis-open.org/legalruleml/legalruleml-core-spec-v1.0/os/legalruleml-core-spec-v1.0-os.html。
- [11] Esteves B, Pandit HJ, Rodríguez-Doncel V. ODRL配置文件：通过在Solid中使用细粒度访问控制策略来表达同意. 收录于：2021 IEEE欧洲安全与隐私研讨会（EuroS PW）；2021. 第298-306页. ISSN: 2768-0657.
- [12] Agarwal S, Steyskal S, Antunovic F, Kirrane S. 立法合规评估：框架、模型与GDPR实例化. 收录于：Annual Privacy Forum. Springer; 2018. 第131-49页.

