# IEDC_floweaver_integration
GitHub repo to document and archive [floweaver Sankey configurations](https://floweaver.readthedocs.io/en/latest/index.html) that work with [industrial ecology data commons (IEDC)](https://www.database.industrialecology.uni-freiburg.de/) datasets

This repository documents the elements of the workflow to establish a traceable IEDC-Sankey link for a given flow dataset from the IEDC. The development goal for 2026 is to set up the infrastructure (web app and supporting services) as well as a fully traceable workflow to generate Sankeys from and link them to their underlying IEDC datasets, with complete metadata and traceability informatin, see this example:

<img width="1311" height="755" alt="IEDC_floweaver_end_result_traceable" src="https://github.com/user-attachments/assets/314a1b13-f6b2-480d-a3f5-0f7040d5df04" />

The IEDC-floweaver integration (offline version and on the web server) is documented in the IEDC handbook: [https://doi.org/10.6094/UNIFR/286224](https://doi.org/10.6094/UNIFR/286224)

**Trace your IEDC-floweaver Sankey**
Each IEDC-floweaver Sankey diagram was created by the IEDC web app by inserting the flow data from an 1_F_xxx dataset into a floweaver Sankey spec file and rendering the result via D3.js. The IEDC dataset id is printed in the traceability statement at the bottom of the figure, and this dataset can be accessed via the [IEDC filtering page](https://www.database.industrialecology.uni-freiburg.de/dataFilter). The floweaver specification id (fss_id) is given there as well, and these ids are defined in the [floweaver IEDC Sankey origin versions config file](https://github.com/IndEcol/IEDC_floweaver_integration/blob/main/floweaver_IEDC_Sankey_configs/floweaver_IEDC_Sankey_origin_versions.json), which makes these specification files traceable by mapping the fss_ids to the generting Jupyter notebooks and floweaver in their respective versions. Finally, the [IEDC Floweaver spec mapping](https://github.com/IndEcol/IEDC_floweaver_integration/blob/main/floweaver_IEDC_Sankey_configs/floweaver_IEDC_Sankey_links.json) links IEDC datasets to the different floweaver Sankey specifications. This mapping can be material-specific and “many-to-many”, —meaning that a Sankey spec can be used for any number of IEDC data sets, and an IEDC data set can be plotted using any number of Floweaver specs.

## Data and programming workflow, overview. 
For details, please check the [IEDC handbook](https://doi.org/10.6094/UNIFR/286224).

**„Offline“ part:**
- Format the flow data from its original source into an IEDC Sankey 1_F xlsx IEDC template (best: download an existing dataset and modify accordingly) and validate the template against the IEDC classifications. Create new IEDC labels (classification items) if needed. Optional: Add a reference flow for showing the scale of the Sankey flow as in the following example.  
- Program the floweaver Sankey by adapting a suitable .ipynb template from the GitHub repo  and link it to the validated 1_F flow data xlsx template (by reading this template into the .ipynb and drawing the Sankey directly from the template, see the examples on GitHub). We provide a Jupyter floweaver template that works with the IEDC upload template in the main directory of the GitHub repository, and this should always be the starting point for new Sankeys.  
- Choose suitable colors and flow aggregations
- Optional: Create several Sankey versions for the same dataset

**„Online“ part:**
Archive the Python code, register a new floweaver .json configuration, and define the link to specific IEDC datasets via GitHub  via the following steps:
- Copy the Jupyter notebook to the archive folder  and commit.
- Register the name(s) of the Sankey configuration(s) in the floweaver specification registry file in the GitHub repo,  by choosing a suitable floweaver Sankey specification (fss) ID and by adding a new entry following the given pattern/example to document the origin and floweaver version of each configuration. The floweaver version can be the GitHub commit ID or the version tag. 
- Link the new json Sankey specification to the relevant IEDC dataset by adding a link in the IEDC-Sankey linking file on GitHub.
- Upload the validated 1_F template to the IEDC, this happens via the IEDC team.
- Compile the floweaver .json configuration(s) from the Jupyter notebook (see the default code at the end of the Jupyter notebook template).
- Upload the floweaver .json(s) to the IEDC web server and commit the updated IEDC dataset-to-Sankey-config matching .json and the floweaver Sankey specification registration .json to the IEDC_floweaver GitHub repository -> The Sankeys can now be generated in the web browser!

**Documentation part:**
- Switch the material, time, region, etc. labels in the .ipynb so that it works with the xlsx dataset downloaded from the IEDC. (change of column labels needed, see examples)
- Copy the modified .ipynb to the IEDC-floweaver GitHub repo, commit. The Sankey configs are now available for public use, and can be modified by the users.

## Background 

Sankey diagrams are a data visualisation technique that shows a system of flows from one process to another, in which the width of the arrows is proportional to the flow rate of the depicted extensive property.  They are an important visualisation technique for MFA systems and widely applied in our community. Among the different software tools that are available for creating Sankey diagrams from MFA datasets,  the floweaver Sankey generator package  sticks out because 
- It origins from our community – floweaver is developed and maintained by Rick Lupton (U Bath, UK) and several contributors.
- It’s a great Sankey tool! Floweaver takes a systematic approach to the structure of the input data (building on the general data model of an MFA flow as material-origin-destination) and the programming of the Sankey diagram’s structure and features, with automatic aggregation of nodes and flows, the option to loop back flows for material cycle diagrams, introducing waypoints (cross-sections) into the diagram, a flexible approach to specifying the layout of the Sankey, and several more.
- It is programmed in Python, a modular and versatile programming language that is widely used in the IE/MFA community.
- It’s open source and version-managed on GitHub and comes with substantial training material.
- It is modular and can be embedded in web applications via the D3.js library.
- A number of great implementations for MFA already exist, many of them from the IE/MFA community, and there is an active community of users.
- It’s documented in a journal publication and comes with an extensive documentation and set of [tutorials](https://floweaver.readthedocs.io/en/latest/index.html). 

So, it’s time to link floweaver to the IEDC!
The floweaver-IEDC-link was developed in 2026 with the following goals:
- Offer an open and interactive web-based platform to find, inspect, and download MFA data alongside with their Sankey visualisations
- Develop a systematic, transparent, traceable, and reproducible workflow to collect both, MFA data and their Sankey visualisations, from the literature
- Contribute to collecting a critical mass of both MFA results and Sankeys to making this collection a useful resource for the community and to building a code base for good Sankey visualisations.
vImplement a few additions to floweaver Sankeys, including the automatic display of a caption, a color legend, a reference flow to show the scale of the values shown, a license statement, and a traceability statement.

