You can also add custom infoType detectors in the Custom infoTypes section, and customize both built-in and custom infoType detectors in the Inspection rulesets section.

# Custom infoTypes

Be aware that any custom infoType detector you create is specific to this workflow and cannot be reused elsewhere. The only exception is Stored infoType, which requires that you create the stored custom infoType detector before specifying it.

To add a custom infoType detector, do the following:

+   1. Click Add custom infoType.

+   2. Choose the type of custom infoType detector you want to create:

+   **Words or phrases:** Matches on one or more words or phrases that you enter into the field. Use this custom infoType name when you have just a few words or phrases to search for. Give your custom infoType name, and then type the word or phrase you want custom DLP to match. To search for multiple words or phrases, press Enter after each one.

+   **Dictionary path:** Searches your content for items in lists of words and phrases. The list is stored in a text file in Cloud Storage. Use this custom infoType when you have anywhere from a few to several thousand words or phrases to search for. This method is also useful if your list contains sensitive elements and you don't want to store them inside of a job or template. Give your custom infoType name, and then, under Dictionary location, enter or browse to the Cloud Storage path where the dictionary file is stored.

+   **Regular expression (regex):** Matches content based on a regular expression. Give your custom infoType name, and then, in the Regex field, enter a regex pattern to match words and phrases. See the supported syntax in Google Cloud documentation at https://pack.link/DRR06.

+   **Stored infoType:** This adds a stored dictionary detector, which is a kind of detector that is built from either a large text file stored in Cloud Storage or a single column of a BigQuery table. Use this custom infoType when you have anywhere from several hundred thousand to millions of words or phrases to search for. Be aware that this is the only option in this menu which you must have already created the stored infoType to use it. Give your custom infoType name (different from the name you gave the stored infoType), and then, in the Stored infoType field, enter the name of the stored infoType.

+   3. Click Add custom infoType again to add additional custom infoType detectors.

Now let us see how to use rulesets to customize the infoTypes to match your requirements. This helps you to avoid false positives.