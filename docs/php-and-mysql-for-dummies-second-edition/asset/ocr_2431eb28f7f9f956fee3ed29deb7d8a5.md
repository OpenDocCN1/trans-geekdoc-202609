On all these pages, a line at the top reads `Click on any picture to see a larger version`. If the customer clicks the picture, a larger version of the picture is displayed.

# Adding pets to the catalog

The application includes three pages that customers don’t see; these are the pages used to add pets to the Pet Catalog. The three pages work in sequential order to add a single pet:

+   1. **Get pet type page.** The person adding a pet to the catalog selects the radio button for the pet type. The user can also enter a new pet type.
+   2. **Get pet information page.** The user selects the radio button for the pet being added and fills in the pet description, price, and picture filename. The user can also enter a new pet name.
+   3. **Feedback page.** A page is displayed showing the pet information that was added to the catalog.

# Get pet type page

The first page gets the pet type for the pet that needs to be added to the catalog. Figure 11-6 shows the get pet type page. Notice that all the pet types currently in the catalog are listed, and a section is provided where the user can enter a new pet type if it’s needed.

# Get pet information page

Figure 11-7 shows the second page. This page lets the user type the information about the pet that goes in the catalog. This page lists all the pet names in the catalog for the selected pet type so that the user can select one. It also provides a section where the user can type a new pet name if needed.

# Feedback page

When the user submits the pet information, the information is added to the `PetCatalog` database. Figure 11-8 shows a page that verifies the information that was added to the database. The user can click a link to return to the first page and add another pet.

# Get missing information page

The application checks the data to see that the user entered the required information and prompts the user for any information that isn’t entered. For instance, if the user selects New Category on the first page, the user must type a category name and description. If the user doesn’t type the name or the description, a page is displayed that points out the problem and requests the information. Figure 11-9 shows the page that users see if they forget to type the category name and description.