```
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

Listing 6: Data altruism form where data subject Anne consents to the usage of their location data for the altruistic purpose of improving mobility.

# 4.3. Uniform, Machine-readable Data Altruism Form

As already proven by the examples provided in the former two subsections, the identified vocabularies, as well as the one we developed ourselves, can also be used to automate the production of consent forms for data subjects and permission forms for data holders. By relying on such technologies by design, the European data altruism forms will promote interoperability and can be reused throughout the EU. An example of a consent form, using the term, EuropeanDataAltruismConsentForm, by a data subject is provided in Listing 6. In this example, we use an altruistic purpose for processing defined in our vocabulary. As such, we define DataAltruism as a subclass or dpv:Purpose and we specify seven new purposes that can be used in a data altruism setting: ImproveHealthcare, CombatClimateChange, ImproveTransportMobility (used in Listing 6), ProvideOfficialStatistics, ImprovePublicServices, ScientificResearch and PublicPolicyMaking. Additional purposes, mentioned throughout the DGA, are also provided in the ad-hoc vocabulary. Similarly, in Listing 7, we provide an example of a permission form of a data holder.

# 5. Discussion

A complete list of all defined terms is available at https://w3id.org/dgaterms, under an open and permissive licence. The analysis of how semantic technologies can be used to operationalise the DGA yields some promising applications, however, a number of hindrances can be identified. Among the advantages, the following ones should be carefully noted:

+   - Semantic technologies can help forge a common understanding of the provisions in the regulation.
+   - Machine-readable policies can be effectively represented in RDF, and executed with appropriate reasoners.