
In addition to these, to specify data users, public sector bodies, competent bodies and single information point providers, we added four new classes of entities (as subclasses of dpv:LegalEntity) to our vocabulary to represent these terms, DataUser, PublicSectorBody, DataReuseCompetentBody, and SingleInformationPointProvider, respectively. EU, national, regional, local and sectorial-level single information point providers are also modelled as subclasses of SingleInformationPointProviders, as depicted in DGA’s Article 8. To be able to classify the nature of the data held by public sector bodies, as specified in Article 3.1, we also added four new subclasses of dpv:Data, ConfidentialData, CommerciallyConfidentialData, StatisticallyConfidentialData and IntellectualProperty to represent data protected through CommercialConfidentialityAgreements or through StatisticalConfidentialityAgreements and data protected by intellectual property rights.

Moreover, the following legal basis for the transfer of public sector body-held data, as specified in Article 5, are also included in our vocabulary, as subclasses of dpv:DataTransferLegalBasis: A5-9 for permissions to transfer, A5-11 for model contractual clauses, and A5-12 for adequacy decisions. DataReusePolicy, DataTransferNotice and ThirdCountryDataRequestNotice concepts were also added, as subclasses of DPV’s policy and notice concepts, to represent the conditions for reuse of data and the notice provided to the owners of said data. As there were no concepts identified to model the searchable asset list maintained by the SingleInformationPointProviders and the procedure to request datasets, both concepts were modelled as DataAssetList and as DataReuseRequestProcedure and as subclasses of dpv:OrganisationalMeasure.

To showcase the usage of existing and newly created terms, an example DataReusePolicy for reusing the http://example.com/dataset_001 dataset, that can be used until the end of 2023 for the purpose of ScientificResearch, can be found in Listing 1⁵. It is modelled as an ODRL offer as it proposes the terms of usage of the dataset, but does not grant any privileges to the data user. Said policy can be used by single information point providers to maintain an updated list of available assets and the conditions for their usage. Listing 2 provides an example of a DataAssetList published by a SingleInformationPointProvider, using the existing and newly created terms. This list contains the previously mentioned dataset, http://example.com/dataset_001, with additional metadata regarding the category of data it contains, the policy that governs its usage, http://example.com/policy_001, the format and size of the data and the fees charged by the publisher of the dataset.

## 4.2. Querying public registers of data intermediaries

As described in Section 2.2, data intermediation service providers and data altruism organisations need to submit information about their activity to a public register of such entities in order to have a centralised database of entities, which can be used by data users, data holders or data subjects to retrieve or publish data, for instance for altruistic purposes.

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dcat: <http://www.w3.org/ns/dcat#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX odrl: <http://www.w3.org/ns/odrl/2/>
PREFIX dpv: <https://w3id.org/dpv#>
PREFIX dpv-pd: <https://w3id.org/dpv/dpv-pd#>
PREFIX dpv-gdpr: <https://w3id.org/dpv/dpv-gdpr#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX ex: <http://example.com/>
PREFIX : <http://anon/dgaterms#>

ex:policy_001 a odrl:Offer, :DataReusePolicy ;
    odrl:permission [
        odrl:target ex:dataset_001 ; odrl:action :Reuse ;
        odrl:assigner ex:publicsectorbodyX ;
        odrl:constraint [
            odrl:and [
                odrl:leftOperand odrl:dateTime ;
                odrl:operator odrl:lteq ;
                odrl:rightOperand "2023-12-31"^^xsd:date ], [
                odrl:leftOperand odrl:purpose ;
                odrl:operator odrl:isA ;
                odrl:rightOperand :ScientificResearch ] ] ] .
ex:publicsectorbodyX a :PublicSectorBody ;
dpv:hasName "Public Sector Body X" ;
dpv:hasContact "mailto:publicsectorbodyX@email.com" ;
:hasCompetentBody [
    a :DataReuseCompetentBody ; dpv:hasName "Competent Body X" ;
    dpv:hasContact "mailto:competentbodyX@email.com" ] .
```

Listing 1: ODRL Offer policy set by the Public Sector Body X that permits the re-use of a dataset until the end of 2023 for scientific research.

```
ex:SIPPA_assets a :DataAssetList, dcat:Catalog ;
    dct:description "Asset list maintained by SIPPA" ;
    dct:created "2022-12-10"^^xsd:date ;
    dct:publisher ex:SIPPA ; dcat:dataset ex:dataset_001 .
ex:SIPPA a :SingleInformationPointProvider .
ex:dataset_001 a dcat:Dataset ; dct:publisher ex:publicsectorbodyX ;
    dpv:hasData :StatisticallyConfidentialData ;
    dct:description "Dataset with statistically confidential data" ;
    dct:created "2022-12-04"^^xsd:date ;
    odrl:hasPolicy ex:policy_001 ; :hasFee "0€"^^xsd:string ;
    dcat:mediaType <iana.org/assignments/media-types/text/csv> ;
    dct:extent "5.6MB"^^xsd:string .
```

Listing 2: Data asset list maintained by the Single Information Point Provider A.

```
1 ex:publicregistry_DI_PT a :RegisterOfDataIntermediationServiceProviders ;
2     dct:description "Public register of intermediaries working in PT" ;
3     dct:created "2023-12-15"^^xsd:date ;
4     dct:modified "2023-12-23"^^xsd:date ;
5     dct:publisher ex:nationalauthority_PT ;
6     :hasDataIntermediationServiceProvider ex:DISP_Y .
7 ex:nationalauthority_PT a :DataIntermediationAuthority ;
8     dpv:hasName "Data Intermediation Authority of Portugal" ;
9     dpv:hasContact "mailto:nationalauthority_PT@email.com" ;
10    dpv:hasJurisdiction "PT" .
11 ex:DISP_Y a :DataCooperative ;
12    dpv:hasName "Data Cooperative Y" ; dpv:hasAddress "Lisboa, Portugal" ;
13    dct:description "Provider of anonymised geolocation data" ;
14    dcat:landingPage <http://cooperativeA.com/> ;
15    dct:date "2023-12-23"^^xsd:date .
```

Listing 3: Example of a public register of data intermediation service providers.

Using the existing and the newly created terms, an example of a register of data intermediation service providers can be found in Listing 3. Due to restrictions in the size of this publication, we do not provide an example of a public register of a data altruism organisation, as both types of public registers contain similar information and will have similar semantic representations. The register ex:publicregistry_DI_PT will have a complete list of intermediaries operating in Portugal. Beyond the stored metadata regarding the national authority ex:nationalauthority_PT and creation dates, the register has already a registered DataCooperative company: ex:DISP_Y.

DPV's hasName, hasContact and hasAddress and DCAT's landingPage can be used to provide information about the providers of data intermediation or data altruism services, while DCT's description, created, and publisher, can be used to describe metadata about the register, including its creation date and its publisher. In addition to these terms that can be reused from existing standards and specifications, to specify a data intermediation service provider (as a subclass of dpv:LegalEntity), or one of its types, we added four new classes of entities to our vocabulary to represent these terms, DataIntermediationServiceProvider, DataCooperative, DataIntermediationServiceProviderForDataHolder, and DataIntermediationServiceProviderForDataSubject. Moreover, data altruism organisations are modelled as a subclass of dpv:NonProfitOrganisation. Information related to the nature of the entity, as specified in Article 11.6(b), to represent the legal status, form, ownership structure, subsidiary and registration number of an entity, is out of the scope of this contribution as it refers to organisational details. However, as a future contribution, upper ontologies such as GIST [17] or Schema.org [18] can be explored, and if necessary extended, to include such concepts.

Furthermore, a PublicRegister class was also added to our vocabulary, and its respective subclasses RegisterOfDataIntermediationServiceProviders and RegisterOfDataAltruismOrganisations to represent public registers of
