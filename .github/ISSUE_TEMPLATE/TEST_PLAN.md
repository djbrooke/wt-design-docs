.github/ISSUE_TEMPLATE/TEST_PLAN.md
---
name: "Release test"
about: Perform a full test for a new release of the WholeTale Platform
title: ''
labels: ''
assignees: ''

---

# Test Plan

https://github.com/whole-tale/wt-design-docs/issues/new?template=TEST_PLAN.md

Note: For all tests, repeat for supported browser/OS combinations.

Preconditions:
* Clear browsing history or open incognito/private session
* Disconnect all third party integrations

## Splash page

* [ ] 
1. Goto https://dashboard.stage.wholetale.org
1. Confirm Terms of Service link
1. Confirm acknowledgements (NSF, XSEDE/Jetstream, Stata)
1. Confirm partner logos


## Authentication

* [ ] Basic login flow
1. Goto https://dashboard.stage.wholetale.org
1. Select "Access Whole Tale" button. You should be prompted to login via Globus Auth.
1. Select your organization and login 
1. You should be taken to the "My Tales" page
1. Your Gravatar should display in the upper right


* [ ] Basic logout flow
1. Select the "User" menu
1. Select the "Log out" menu item. You should be taken to the login page.
1. Select "Access Whole Tale" button. 
1. Note that you are not prompted to login. 
1. Restart your incognito session
1. Select "Access Whole Tale" button.  You should be prompted to login via Globus Auth.


* [ ] Return-route for non-logged in users
1. Logout from Whole Tale
1. Attempt to access  https://dashboard.stage.wholetale.org/public
1. You should be redirected to https://dashboard.stage.wholetale.org/login?rd=%252Fpublic
1. Select "Access Whole Tale".
1. You should be redirected to the "Public Tales" page.


## Navigation

* [ ] General navigation
1. Select "Tale Dashboard" link. "My Tales" page should display
1. Click "Create New Tale" > "Create New Tale". The Create Tale modal should display. Click "Cancel" to close the modal
1. Select the "i" icon at the upper right corner; it should open the User Guide in new tab
1. Select the "Notification" button next to the "i" icon; it should display the notification panel
1. Select the "bug" icon; it should open https://github.com/whole-tale/whole-tale/issues in new tab (after authentication)
1. Mouse over a Tale and select "View". The Run page should display
1. Click the "user" icon at the top right
  - You should see a dropdown expand
  - The dropdown should contain the user's first/last name and gravatar image
  - The dropdown should provide a link to the Settings page
  - The dropdown should provide an option to Logout
  - Select the "Settings" option; it should bring you to the Settings page


## Tale Dashboard

Preconditions:
* Assumes production Tales present (e.g., LIGO, materials, etc).
* No running instances


* [ ]  General
1. Select "My Tales" link. Confirm "My Tales" page displays
1. Confirm that no Tales are running
1. Select "Shared with Me" link. Confirm "Shared with Me" page displays

* [ ] Search
1. Select "Public Tales" link. Confirm "Public Tales" page displays
1. Enter "LIGO" as search term. Confirm only LIGO tale displays (by K. Kowalik)
1. Clear search term. Confirm all tales display

* [ ] View tale
1. Select "View" button on LIGO Tale
1. Confirm that Metadata page displays by default
1. Confirm that you cannot delete or edit Tale properties
1. Select Back button. Confirm that you are taken back to Public Tales page
1. Select "View" button on Tale you own
   1. Confirm that the Run and Close buttons are present
   1. Confirm that you can edit Tale properties
   1. Select "Close"
   1. Confirm that you are taken back to "My Tales"


* [ ] Launch instance
1. Select "Run Tale" button on "Ligo" tale
   1. Confirm you are prompted to Copy and Run
   1. Select "Confirm"
   1. Confirm that you are redirected to the Tale's "Metadata" page
   1. Confirm that the "Edit" button is present
   1. Select "Run Tale"
   1. Confirm that the "Interact" page is displayed with spinner
   1. Confirm that the notification dialog appears
   1. Confirm that the step progression is correct
   1. Confirm that the "View Logs" button shows the build logs in a modal
   1. Navigate to the "My Tales" page
   1. Confirm that the Tale is shown under "Currently Running"
   1. Select "View" on the Tale card
   1. Confirm that "Interact" page is displayed
1. Select "Stop" to end the Tale instance
   1. Confirm that the Tale has stopped
   1. Confirm that the button has changed to Run Tale
1. Navigate to "My Tales"
   1. Confirm that there are no Tales under "Currently Running"
   1. Select the "Run Tale" button on a Tale you own
   1. After the instance is launched, navigate back to the My Tales page
   1. Confirm that you cannot select the delete button on the My Tales page
   1. Confirm that the "Run Tale" button has been replaced with "Stop Tale"
   1. Confirm that the Tale is shown at the top of the page under "Currently running"

## Managing Data

Preconditions
* Empty home directory
* No registered data

* [ ] Register General
1. Open an owned Tale
1. Select 'External Data' > "+" > Web (DOI or URL)
1. Confirm list of providers matches list of supported providers (Globus, DataONE, Dataverse, Zenodo)

* [ ] Register DataONE data
1. Open an owned Tale
1. Select 'External Data' > "+" > Web (DOI or URL)
1. Confirm modal displays
1. Search for DOI `10.5065/D6862DM8`
1. Confirm "Humans and Hydrology" dataset is found on DataONE.
1. Select Register
1. Confirm dataset appears in Manage Data list
1. Confirm additional URL formats:
   1. https://search.dataone.org/view/doi:10.5063/F1Z60M87
   1. https://search.dataone.org/view/https://pasta.lternet.edu/package/metadata/eml/knb-lter-nwt/115/1
   1. https://search.dataone.org/view/doi:10.18739/A2CN6XZ7H
   1. https://raw.githubusercontent.com/whole-tale/dashboard/master/.travis.yml


* [ ] Dataverse
1. Register dataset doi:10.7910/DVN/SZ9YXZ
1. Confirm "Replication Data for: Direct Democracy and Women's Political Engagement" from Dataverse


* [ ] Globus/MDF
1. Confirm DOI resolution for http://dx.doi.org/doi:10.18126/M2301J results in https://petreldata.net/mdf/detail/pub_30_shahani_twinmediated_v1.2
1. Register dataset https://petreldata.net/mdf/detail/pub_30_shahani_twinmediated_v1.2


## Run Tale

Preconditions:
* No running Tale instances

* [ ] General
1. On "Public Tales", click "Run" on LIGO tale (Copy on Launch)
1. Select "Run Tale" to start the instance
1. Confirm you are redirected to the Run page
   1. Confirm that the Run panel displays the Tale icon, title, and author
   1. Confirm that the Run page displays the Interact, Files, Metadata tabs
   1. Confirm that Interact tab is displayed by default
   1. Confirm notification panel displays and progression is correct
1. Select the "..." menu. 
   1. Confirm that menu options exist for "Rebuild Tale", "Restart Tale", "Save Tale Version", "Duplicate Tale", "Publish Tale", "Export Tale", "Connect to Git Repository..."
   1. Confirm that the "Read the docs" link displays https://wholetale.readthedocs.io/en/latest/users_guide/run.html in a new tab or window (stable is for production)
   1. Confirm that the "View Fullscreen" link displays the Run panel in full screen

* [ ] Interact tab
1. Select the "Interact" tab
1. Confirm Jupyter environment is displayed in iframe 
1. Select "popout" icon. Confirm Jupyter is opened in new Tab

* [ ] Files tab
1. Select "Files" tab
1. You should see a vertical navigation menu with three tabs: "Home", "External Data", and "Tale Workspace".
1. Confirm Tale Workspace is selected by default

* [ ] Metadata tab - Owned Tale
1. Open a Tale that you own (e.g., LIGO Tale copy)
1. Navigate to the Metadata tab
1. Confirm that your Tale has the CC4 license assigned to it
1. Confirm that the Tale's `Published Location` reads `This Tale has not been published`
1. Note "Datasets Used: No citable data"
1. Add multiple dataset via External Datasets (Humans and Hydrology, Replication Data for Direct Democracy...)
1. Navigate to Run > Metadata
1. Confirm that there are citations for the external datasets
1. Click the "Edit" button to edit the metadata fields
1. Confirm editable fields (Title, Authors, Category, Environment, License, Description, Illustration)
1. Valid environments should be listed in the `Environment` dropdown menu
1. Valid licenses should be listed in the `License` dropdown (CC4 and CC0)
1. Change the name of the Tale, Category, Description, Illustration, Public, License, and add multiple authors 
1. Select Save. Confirm that you see a notification telling you that the Tale was saved.
1. Confirm that changes are reflected in the page.
1. Refresh the page. Your changes should be preserved between page refreshes, confirming that they are being properly persisted.
1. Confirm that the new Tale authors are displayed on the Tale card

* [ ] Metadata tab - Non-Owned Tale (e.g., Public LIGO Tale)
1. Open a Tale that you don't own
1. Navigate to the metadata page
1. Note that there isn't an 'Edit' button present
1. Confirm read-only fields (Title, Created By, Authors, Category, Environment, License, Description, Datasets Used, Related Identifiers, Publised Location, Date Created, Last Updated)

* [ ] Home
1. View a tale that you own
1. Select Files > Home. Confirm that your home directory displays
1. Create a folder and upload a file to the folder
1. Confirm file operations: Copy, rename, remove, download, Move To...
   1. Copy file/folder
   1. Rename file/folder
   1. Download file/folder
   1. Upload file / create folder with duplicate name
   
* [ ] External data
1. Precondition: Register one or more Datasets (e.g. `doi:10.18739/A29G5GD0V`)
    1. Confirm notification progress and success
1. Create a new tale
1. Confirm "External Data" list is initially empty
1. Confirm (+) button ("Select Data modal") behavior
    1. Confirm that "WT Data Catalog" shows all registered datasets
    1. Confirm that "My External Data" filters to only show your registered datasets
    1. Select a dataset
    1. Confirm that clicking "Add Selected" adds the dataset to the "Selected Data" column
    1. Confirm that "Remove Selected" data to dissociate it with a Tale
    1. Using the dataset above, add the dataset to the Tale, by clicking "Save"
    1. Confirm that the Tale's "External Data" list matches what was saved
    1. Remove the dataset from the Tale
    1. Confirm "External Data" list matches what was saved
    1. Select a dataset but then click out of the modal or click "Cancel"
    1. Confirm that the changes weren't saved

* [ ] Tale Workspace
1. Confirm create folder
1. Confirm upload file
1. Select "+" button has options "New folder", "Upload file", "Select Data..."
1. Folder operations
   1. Confirm context menu Copy, Rename, Download, Remove
   1. Confirm rename folder
    1. Confirm download folder (this should result in a zip file) 
    1. Confirm remove folder
1. File operations
   1. Upload a file
   1. Confirm context menu Copy, Rename, Download, Remove
   1. Confirm rename file
    1. Confirm download file
    1. Confirm remove file
1. Select "Select Data..."
   1. Note vertical navigation with Tale Workspaces
   1. Copy to Workspace from another workspace 
   1. Move to workspace from another workspace

* [ ] Files - Non-Owned Tale
1. Open a Tale that you don't have write permissions to
1. Attempt to add data to the workspace and external data
1. Note that the "+" icons are greyed out, preventing you from doing so
1. Note that Home directory isn't present

* [ ] Export Tale
1. Open your copy of the LIGO Tale or import https://girder.stage.wholetale.org/api/v1/integration/zenodo?doi=10.5281%2Fzenodo.490449&resource_server=sandbox.zenodo.org
1. Select "Export Tale" from Tale menu
1. Confirm that a download starts for the ZIP archive
1. Open the archive
1. Confirm that exported ZIP is a valid Bag
   1. Must contain bagit.txt, bag-info.txt
   1. Optionally `pip install bdbag` and `bdbag --validate full .`
1. Run the exported tale and confirm that it builds and runs as expected 
   1. Follow instructions in README.md

## Settings

* [ ] Default State
1. Navigate to the Settings page
1. Confirm there are empty settings for DataONE, Dataverse, and Zenodo

* [ ] Connect to Zenodo
1. Click "Connect Account" in the Zenodo section
1. Confirm that the connection modal opens
1. Confirm that sandbox.zenodo.org and zenodo.org are listed
1. Select sandbox.zenodo.org from repository list
1. Select "Get from Zenodo"
   1. Login to Zenodo if necessary
   1. Create token
   1. Copy token
1. Enter your API key into WT modal
1. Click "Connect"
1. Confirm that you see "Authorized on <server>"
1. Select disconnect, confirmation window should appear
1. Repeat test with invalid key, confirm error message appears
1. Repeat for each Zenodo server
1. Confirm "Get from" link matches selected repo

* [ ] Connect to Dataverse
1. Click "Connect Account" in the Dataverse section
1. Confirm that the connection modal opens
1. Enter your API key for one of the repositories
1. Click "Connect"
1. Confirm that you see "Authorized on <server>"
1. Select disconnect, confirmation window should appear
1. Repeat test with invalid key, confirm error message appears
1. Repeat for each Dataverse server
1. Confirm "Get from" link matches selected repo

* [ ] Connect to DataONE
1. Click "Connect Account" under the DataONE repository
1. Confirm that the connection modal opens
1. Enter your JWT for one of the repositories
1. Confirm that you see "Authorized on <server>"
1. Select disconnect, confirmation window should appear
1. Repeat test with invalid key, confirm error message appears
1. Repeat for each DataONE server

* [ ] Confirm tokens retained across logins
  [#370](https://github.com/whole-tale/girder_wholetale/pull/370)
1. Connect one or more accounts as outlined above
1. Logout and login again
1. Using Swagger UI, hit the `/user/me` endpoint to confirm tokens are still present


## Tale Creation

* [ ] Create JupyterLab Tale
1. Select the Create New Tale button on the 'Browse' page
1. Enter title "Test Tale"
1. Select JuptyerLab environment
1. Select "Create New Tale"
1. Confirm that you're brought to the 'Metadata' page and the "Run Tale" button is visible
1. Click "Run Tale"
1. Confirm notification dialog opens and progress order is correct
1. Confirm that you are redirected to "Interact" tab with Tale launching spinner
1. During build image step, select View Logs. Confirm logs are accessible.
1. Wait for launch to complete
1. Select "Return to Dashboard"
1. Confirm the Tale is shown under "Currently running"
1. Select "View", confirm that the interact tab is displayed with JupyterLab IDE 
1. Select popout icon and confirm that JupyterLab IDE displays
1. Stop and delete the tale


* [ ] Create RStudio Tale
1. Create tale from Git repo https://github.com/whole-tale/rstudio-example/
1. Select environment RStudio 4.0.2
1. Run tale and confirm RStudio IDE displays in iframe and works in popout
1. Open Code/1_credit_permissiveness.R
1. Confirm outputs are created in Outputs without error

* [ ] Compose Jupyter Notebook Tale
1. Create tale from Git repo https://github.com/whole-tale/jupyter-example/
1. Select environment Jupyter Notebook
1. Run tale and confirm Jupyter Classic IDE displays in iframe and works in popout
1. Add usco2005.xlsx from Humans and Hydrology dataset
1. Run notebook, confirm it produces most glorious map of Texas

* [ ] Compose JupyterLab Tale
1. Create tale from Git repo https://github.com/whole-tale/jupyter-example/
1. Select JupyterLab environment
1. Run tale and confirm JupyterLab IDE displays in iframe and works in popout
1. Confirm JupyterLab IDE displays
1. Add usco2005.xlsx from Humans and Hydrology dataset
1. Run notebook, confirm it produces most glorious map of Texas

* [ ] Compose JupyterLab with Spark
1. Create tale from Git repo https://github.com/whole-tale/spark-example/
1. Select Jupyter with Spark environment
1. Run tale and confirm JupyterLab IDE displays in iframe and works in popout
1. Run notebook and confirm version is 2.4.3

* [ ] Compose MATLAB Desktop Tale
1. Create tale from Git repo https://github.com/whole-tale/matlab-example/
1. Select MATLAB Desktop environment
1. Run tale and confirm MATLAB Web Desktop IDE displays in iframe and works in popout
1. Open and run `multiplicative_arima_example_script.m`, confirm outputs
1. Open and run `multiplicative_arima_example_livescript.m`, confirm outputs

* [ ] Compose MATLAB Jupyter Kernel Tale
1. Create tale from Git repo https://github.com/whole-tale/matlab-example/
1. Select MATLAB Jupyter Kernel environment
1. Run tale and confirm JupyterLab IDE displays in iframe and works in popout
1. Open and jun `multiplicative_arima_example.ipynb`, confirm outputs match `multiplicative_arima_example.html`

* [ ] Compose MATLAB Linux Desktop Tale
1. (Only test if present)
1. Create tale from Git repo https://github.com/whole-tale/matlab-example/
1. Run tale and confirm Xpra-based MATLAB IDE displays in iframe and works in popout
1. Open and run `multiplicative_arima_example_script.m`, confirm outputs

* [ ] Compose STATA Desktop Tale
1. Create tale from Git repo https://github.com/whole-tale/stata-example/
1. Run tale and confirm Xpra-based STATA IDE displays in iframe and works in popout
1. Run `example.do`, confirm outputs

* [ ] Compose STATA Jupyter Kernel Tale
1. Create tale from Git repo https://github.com/whole-tale/stata-example/
1. Run tale and confirm JupyterLab IDE displays in iframe and works in popout
1. Run `example.ipynb`, confirm outputs match `example.html`

* [ ] Compose OpenRefine Tale
1. Create a new tale based on the OpenRefine environment
1. Run tale and confirm OpenRefine IDE displays in iframe and works in popout

* [ ] Too many instances
1. Run 2 tales
1. Attempt to run another Tale
1. Confirm that you receive an error that you have the max limit

## Analyze in Whole Tale

These test cases cover potential situations that can occur when importing datasets from Dataverse.

* [ ] Import dataset from Dataverse
 1. Remove all running Tale instances
 1. Navigate to https://girder.stage.wholetale.org/api/v1/integration/dataverse?datasetPid=doi%3A10.7910%2FDVN%2F3MJ7IR&siteUrl=https%3A%2F%2Fdataverse.harvard.edu
 1. Confirm that the Tale title reads as ``Replication Data for: "Agricultural Fires and Health at Birth"``
 1. Confirm that the only item in the ``Input data`` section matches the uri with ``Data Source`` appended 
 1. Confirm that no environment is selected
 1. Confirm that the ``Create New Tale`` button is disabled
 1. Select an environment
 1. Confirm that READ/WRITE is selected
 1. Click ``Create New Tale``
 1. Confirm registration notification progress and success
 1. Confirm that you are redirected to the Metadata page and "Run Tale" is enabled
 1. Confirm that the Tale name matches the Tale Name in the Create Tale Modal
 1. Confirm that the data exists under Tale Workspace
 1. Confirm that the Tale's category is `science`

* [ ] Import dataset from DataONE: READ-ONLY
 1. Remove all running Tale instances
 1. Navigate to https://girder.stage.wholetale.org/api/v1/integration/dataone?uri=https%3A%2F%2Fsearch.dataone.org%2Fview%2Fdoi%3A10.18739%2FA2VQ2S94D&title=Fire%20influences%20on%20forest%20recovery%20and%20associated%20climate%20feedbacks%20in%20Siberian%20Larch%20Forests%2C%20Russia&environment=RStudio
 1. Confirm that the Tale title reads as ``Fire influences on forest recovery and associated climate feedbacks in Siberian Larch Forests, Russia``
 1. Confirm that the only item in the ``Selected data`` section matches the uri with ``Data Source`` appended
 1. Confirm that ``Rstudio`` is selected in the Environments widget
 1. Confirm that the ``Create New Tale`` button is enabled
 1. Confirm READ ONLY is selected
 1. Click ``Create New Tale``
 1. Confirm that you are redirected to the Metadata tab
 1. Confirm that the Tale name matches the Tale Name in the Create Tale Modal
 1. Confirm that the data exists in the Tale under External Data
 1. Confirm that the Tale's category is `science`
 1. Confirm that the Datasets Used and Related Identifiers are updated to reflect the dataset 

* [ ] Import from DataONE: READ-WRITE
 1. Navigate to https://girder.stage.wholetale.org/api/v1/integration/dataone?uri=https%3A%2F%2Fsearch.dataone.org%2Fview%2Fdoi%3A10.18739%2FA2VQ2S94D&title=Fire%20influences%20on%20forest%20recovery%20and%20associated%20climate%20feedbacks%20in%20Siberian%20Larch%20Forests%2C%20Russia&environment=RStudio
 1. Confirm that the Tale title matches the dataset
 1. Confirm that the only item in the ``Selected data`` section matches the uri with ``Data Source`` appended
 1. Confirm that the ``Create New Tale`` button is disabled
 1. Select `READ/WRITE`
 1. Click ``Create New Tale``
 1. Confirm that the notification bar appears & properly updates
 1. Confirm that you are redirected to the run page
 1. Confirm that the Tale name matches the Tale Name in the Create Tale Modal
 1. Confirm that the data exists in the Tale Workspace

* [ ] Import from DataONE: alternate sites
  1. "proveit": https://dashboard.stage.wholetale.org/browse?api=https%3A%2F%2Fcn-stage-2.test.dataone.org%2Fcn%2Fv2&name=Dataone%20Dataset&uri=https://dev.nceas.ucsb.edu/view/doi:10.5072/FK2K075M25
  1. "Alpha Helix 2001...": https://dashboard.stage.wholetale.org/browse?api=http%3A%2F%2Fcn-stage.test.dataone.org%2Fcn%2Fv2&name=Dataone%20Dataset&uri=https://test.arcticdata.io/view/doi:10.5065/D6N014NC
  1. Remove all running Tale instances
  1. Navigate to each of the two links above
  1. Select an environment
  1. Click ``Create New Tale``
  1. Confirm that the correct data exists in the Tale under External Data

* [ ] Import from Zipfile
  1. Export a tale you own or copy of LIGO tale
  1. Import via API
```
export GIRDER_TOKEN=<your token>
curl -X POST -H "Content-Type: application/zip" --data-binary "@<path-to-zip>.zip" --header 'Girder-Token: ${GIRDER_TOKEN}' 'https://girder.local.wholetale.org/api/v1/tale/import'
```
  1. Confirm tale imports, builds and run
  1. Try with invalid token: (You must be logged in)
  1. Try with invalid zipfile (Bad bag)

## Tale metadata tests
The purpose of these tests are to confirm that the metadata files (manifest.json, environment.json, LICENSE) we generate are correct.

* [ ] manifest.json
1. Launch a Tale that you own
1. Add a dataset to the Tale
1. Add at least one author
1. Add at least one file to the workspace
1. Create a version
1. Export the Tale (as BagIt)
1. Open the `manifest.json` file under `metadata/`
1. Confirm `wt` context present
1. Confirm `@id` references the correct Tale ID
1. Confirm that the author is listed under `schema:author`
1. Confirm that you are listed under `createdBy`
1. Confirm that the file(s) in the workspace are properly listed in `aggregates`
1. Confirm that the external dataset is referenced in `aggregates`
1. Confirm that the dataset is also listed under `wt:usesDataset`
1. Confirm `dct:hasVersion` is present and matches your created version
1. Optionally confirm `rdflib` can parse:
```
from rdflib import Graph

import urllib.parse
urllib.parse.uses_relative.append('arcp')
urllib.parse.uses_netloc.append('arcp')

g = Graph().parse(source="manifest.json", format="json-ld")
print(g.serialize(format='turtle', indent=2).decode())
```

* [ ] environment.json
1. Open the archive from the manifest.json test
1. Navigate to `metadata/environment.json`
1. Open the girder web API
1. Locate and GET the Image that the Tale used
1. Confirm that the `config` section from girder matches the `config` section in `environment.json`

* [ ] LICENSE
1. Open the archive from the manifest.json test
1. Open the `LICENSE` file
1. Navigate to Run > metadata
1. Confirm that the opened `LICENSE` file matches the selected license on the metadata page
1. Change the Tale's license
1. Export the Tale
1. Confirm that the `LICENSE` changed appropriately

## Tale Sharing Tests

These tests are centered around the feature for sharing Tales with other Whole Tale
users. To run these tests, register at least one other account, referred to as User B.

* [ ] Case 1: Sharing with 'Can View' permissions
  1. Create a new Tale
  1. Add data to the workspace and add at least one dataset
  1. Navigate to the 'Share' tab
  1. Share the Tale with User B
  1. Confirm that the default permission is 'Can View'
  1. Switch the account to User B
  1. Navigate to the 'Shared with Me' tab on the Browse page
  1. Confirm that you see the Tale from step 1
  1. Confirm that you can't edit the Workspace, External Data, or metadata
  1. Unshare tale with User B
  1. Note modal displays that tale has been unshared.

* [ ] Case 2: Sharing with 'Can Edit' permissions
  1. Create a new Tale
  1. Add data to the workspace and add at least one dataset
  1. Navigate to the 'Share' tab
  1. Share the Tale with User B
  1. Set the permissions to 'Can Edit'
  1. Switch the account to User B
  1. Navigate to the 'Shared with Me' tab on the Browse page
  1. Confirm that you see the Tale from step 1
  1. Remove one of the files from the Workspace
  1. Add a dataset to External Data
  1. Change a field in the metadata (title, description, etc)
  1. Switch to User A
  1. Confirm that the changes made to the Tale persisted

* [ ] Case 3: Edit sync modal
  1. Login as User A and User B in separate browser sessions
  1. As User B, select "Shared with me"
  1. As User A, share a tale with User B; as User B confirm the tale appears
  1. As User B, select "View" on the shared tale
  1. As User A and B edit the tale metadata
  1. As User A change title, author, category, description; save changes
  1. As User B confirm Tale edited modal, select Yes, confirm updates to metadata

## Publishing tests

* [ ] Case 1: No Accounts Configured
  1. Disconnect all of your external accounts
  1. Open a Tale that you own
  1. Click the ellipsis dropdown on the Run page
  1. Click `Publish tale...`
  1. Confirm that your are notified to link accounts on the settings page
  1. Click `Go to Settings`
  1. Confirm you are re-directed to settings

* [ ] Case 2: Publishing to DataONE
  1. Connect to DataONE (dev server)
  1. Open a Tale that you own
  1. Add some data to it
  1. Click `Publish tale...`
  1. Confirm that the publishing modal opens
  1. Confirm that the third party that you are connected to appears in the dropdown
  1. Select the third party
  1. Click `Publish`
  1. Once complete, navigate to the metadata page
  1. Confirm that the published location is present
  1. Visit the published location
  1. Confirm that you see the following files plus yours
      1. `metadata.xml`
      1. `LICENSE`
      1. `README.md`
      1. `manifest.json`
      1. `environment.json`
  1. After publishing to DataONE, use girder to query the Tale
  1. Ensure that the 'pid' field in the 'publishInfo' object has an identifier in a doi format

* [ ] Case 3: Re-publish Tale to DataONE
1. Launch a Tale that has been published before
1. Take note of the `Published Location` in Run > metadata
1. Re-publish the Tale to the third party
1. Confirm that the `Published Location` has changed to the correct package landing page

## Zenodo integration tests

* [ ] Register Zenodo data
1. On a new or existing tale, select "Files" > "External Data"
1. Select "+" > "Web (DOI or URL)"
1. Search for Concept DOI `doi:10.5281/zenodo.16384`
1. Confirm "Belmont Forum..." dataset is found on Zenodo with suffix `ver_1`
1. Search for URL  `https://zenodo.org/record/1172960#.XidIvlNKh24`
1. Confirm "Belmont Forum..." dataset is found on Zenodo with suffix `ver_2`
1. Search for DOI `doi:10.5281/zenodo.1172960`
1. Confirm "Belmont Forum..." dataset is found on Zenodo with suffix `ver_2`
1. Search for Concept DOI `doi:10.5281/zenodo.608984`
1. Confirm "Belmont Forum..." dataset is found on Zenodo with suffix `ver_2`
1. Select Register
1. Select "+" > "WT Data Catalog"
1. Add "Belmot Forum..." dataset to Tale
1. Run Tale and confirm contents on file system match Zenodo

The register tests the following cases.
   * Datasets with multiple files
   * Datasets with multiple versions
   * Concept DOI 

* [ ] Zenodo dataset via AiWT
1. Open https://dashboard.stage.wholetale.org/browse?uri=https%3A%2F%2Fdoi.org%2F10.5281%2Fzenodo.820575&name=Automotive%20Sensor%20Data
1. Confirm Source Data URL and Title match above URL and "READ ONLY" is selected
1. Select JupyterLab environment
1. Select 'Create New Tale'
1. Confirm dataset is mounted read-only, citation and related ids are as expected,
1. Run IDE and use terminal to `ls ../data/Auto*` to confirm zipfile is not extracted

The register tests the following cases.
   * Dataset with single file (zipfile)

* [ ] Zenodo Binder via AiWT
1. Open https://dashboard.stage.wholetale.org/browse?uri=https%3A%2F%2Fdoi.org%2F10.5281%2Fzenodo.3242073&environment=JupyterLab&name=Simple%20requirements.txt%20based%20example%20for%20repo2docker&asTale=true
1. COnfirm Source Data and Title match URL and "READ WRITE" is selected
1. Select 'Create Tale'
1. Confirm image builds and notebook can run

* [ ] Zenodo Tale via AiWT
1. Open https://girder.stage.wholetale.org/api/v1/integration/zenodo?doi=10.5281%2Fzenodo.490449&resource_server=sandbox.zenodo.org
1. Confirm Water Tale is created. 
1. Confirm citation on Metadata view
1. Confirm DOI matches above
1. Use the Swagger UI to confirm the `publishInfo` field on the tale object contains pid, repository, repository_id, uri
1. Run the tale and and notebook, confirm it works as expected (produces glorious map of Texas) 

* [ ] Publish/import to/from Zenodo Sandbox
1. Follow instructions above to configure your API key for Zenodo sandbox 
1. Create your own Tale and publish to sandbox.zenodo.org
1. Confirm publishInfo contains Sandbox entry
1. Delete tale
1. Import tale from Zenodo
1. Confirm publishInfo
1. Modify the tale
1. Re-publish to sandbox.zenodo.org
1. Delete tale
1. Import tale from Zenodo
1. Confirm publishInfo
1. Download and extract the exported Tale
1. Execute the `run-local.sh` command to run the Tale locally

## Versioning Tests

* [ ] Tale Versioning
1. View a Tale that you own
1. Expand Tale Version panel (on the right)
1. Create a New Version: `init`
1. Modify metadata, upload a file, and attach a dataset to the Tale
1. Create another new version: `modified`
1. While viewing Run > Files > External Data, restore from `init` - you should see no datasets
1. Rename the `modified` Version to `something else`
1. In the same view, restore back to `something else` - you should see the dataset you added
1. Run the tale. Confirm the versions are available under `../versions` and that the contents including metadata are as expected
1. View Info for a version
1. Rename a version. Confirm rename in container.
1. Export a version. Confirm exported version matches selected version.
1. Delete a version. Confirm deletion in container.

* [ ] Copy versions
1. Login as a user with view-only permissions of a tale with versions.
1. Run the tale and confirm versions are copied

* [ ] Publish/export version
1. Create a new tale
1. Upload files but do not create a version
1. Publish the tale
1. Note that there is a new version in the version panel
1. Confirm that the data files in the published artifact are correct
1. Repeat for export
1. Confirm manifest contents including vocabulary


## Git Integration Tests

* [ ] Compose Tale from Git Repository
Covered by other tests
1. Select the Create New Tale button on the 'Browse' page
1. Select the `Create Tale from Git Repository` option
1. Paste a link to a Git repository in the correct field
1. Add a name and pick a compute environment
1. Create the Tale
1. Confirm notification progress and success
1. Confirm that the git repository was cloned to the `workspace/` root
1. Run the tale
1. Confirm interaction via git tools (may require environment customization)


* [ ] Connect to Git
1. Create a new empty tale
1. Select "Connect to Git Repository" menu item from Tale menu
1. Confirm notification progress and success
1. Once complete, navigate to the Tale workspace and confirm that the repository has been cloned


## Other tests

* [ ] Citations
1. Add files from multiple external datasets (e.g.: doi:10.5281/zenodo.3381658, doi:10.5065/D6862DM8, doi:10.5063/F10K26VR)
1. Confirm `Datasets Used` citations and related identifiers are updated


### Event Notification Tests
* [ ] Tale sharing/unsharing
1. Login as user1 and user2 in separate browser sessions
1. As user2, select "Shared with me"
1. As user1, share a tale with user2; as user2 confirm the tale appears
1. As user2, select "View" on the shared tale
1. As user1 and 2 edit the tale metadata
1. As user1 save changes; as user2 confirm Tale edited modal
1. As user1, unshare the tale; as user2 confirm Tale unshared modal
1. As user1, re-share with user2
1. As user2, select "Shared with Me"
1. As user1, delete the shared tale; as user2 confirm that the tale disappears

* [ ] Import tale
1. Import a tale from Github, Zenodo, and as Binder
1. Confirm metadata updates accordingly after import completes

## Vocabulary Tests

* [ ] Vocabularies
1. Go to https://vocabularies.stage.wholetale.org/wt/1.0/index.html
1. Confirm that it matches https://whole-tale.github.io/serialization-format/wt/1.0/

## Forward Authentication Test
* [ ] Forward authentication
1. Start a tale
1. Confirm that the tale is accessible via iframe and popout
1. Right click popout icon and copy URL (this is necessary to get JupyterLab token)
1. Open an incognito window and paste the copied URL
1. Confirm that you are prompted for authentication and can access the tale once authenciated
1. Login as a user who does not have permission to access the tale
1. Confirm that they receive an access denied errror

## Changing the Environment
* [ ] Changing the environment
1. Create a new JupyterLab tale
1. Run the Tale, confirm JupyterLab IDE displays
1. Edit metadata, change environment to "RStudio"
1. Confirm icon changes in title bar and Environment section
1. Stop/run tale or rebuild/restart and confirm RStudio IDE displays

## Idle Instances
* [ ] Idle instance culling
1. Create and start a MATLAB tale and a JupyterLab tale
1. Confirm both instances start and IDEs are accessible
1. Close all IDE tabs/windows
1. Wait for 2 hours and 24 hours respectively
1. Confirm both instances are stopped automatically
