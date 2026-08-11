# IEDC_floweaver_integration
GitHub repo to document and archive [floweaver Sankey configurations](https://floweaver.readthedocs.io/en/latest/index.html) that work with [industrial ecology data commons (IEDC)](https://www.database.industrialecology.uni-freiburg.de/) datasets

This repository documents the elements of the workflow to establish an IEDC-Sankey link for a given flow dataset from the IEDC. The development goal for 2026 is to set up the infrastructure (web app and supporting services) as well as a fully traceable workflow to generate Sankeys from and link them to their underlying datasets (see example figure):

<img width="1405" height="768" alt="IEDC_floweaver_end_result_traceable" src="https://github.com/user-attachments/assets/5617e24a-4c8b-46fc-8c62-3bbb403e5b21" />



The IEDC-floweaver integration (offline version and on the web server) is documented in the IEDC handbook, which is currently in internal review and will be published in the summer of 2026 via [https://www.database.industrialecology.uni-freiburg.de/](  https://www.database.industrialecology.uni-freiburg.de/)

In the meantime, the following preliminary documenantation is available:

**„Offline“ part:**
- Format the flow data into the IEDC Sankey 1_F xlsx IEDC template and validate the template against the IEDC classifications
    - Create new IEDC labels (classification items) if needed
    - Optional: Add a reference flow for the scaling and color legend flows for the color coding
- Program the floweaver Sankey by adapting the .ipynb template and link it to the validated 1_F flow data xlsx template
    - Choose suitable colors and flow aggregations
    - Optional: Create several Sankey versions for the same dataset

**„Online“ part:**
- Register the Sankey configurations in the [registry file](https://github.com/IndEcol/IEDC_floweaver_integration/blob/main/floweaver_IEDC_Sankey_configs/floweaver_IEDC_Sankey_origin_versions.json)
- Upload the 1_F template to the IEDC via the IEDC team
- From the .ipynb, compile and export the floweaver .json configuration and upload the floweaver .json to the IEDC web server
- Define the link between IEDC dataset and floweaver .json confiiguration in the [link file](https://github.com/IndEcol/IEDC_floweaver_integration/blob/main/floweaver_IEDC_Sankey_configs/floweaver_IEDC_Sankey_links.json) -> The Sankeys can now be generated in the web browser!

**Documentation part:**
- Switch the material, time, region, etc. labels in the .ipynb so that it works with the xlsx dataset downloaded from the IEDC
- Copy the modified .ipynb, the .py Sankey configuration, and the .json pallette to the IEDC-floweaver GitHub repo, commit
