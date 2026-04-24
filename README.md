# IEDC_floweaver_integration
GitHub repo to document and archive floweaver Sankey configurations that work with industrial ecology data commons (IEDC) datasets

This repo documents the elements of the workflow to establish an IEDC-Sankey link for a given flow dataset.

The IEDC-floweaver integration (offline version and on the web server) is documented in the IEDC handbook, available as of summer 2026 via [https://www.database.industrialecology.uni-freiburg.de/](  https://www.database.industrialecology.uni-freiburg.de/)

**„Offline“ part:**
- Format the flow data into the IEDC Sankey 1_F xlsx IEDC template and validate the template against the IEDC classifications
    - Create new IEDC labels (classification items) if needed
    - Optional: Add a reference flow for the scaling and color legend flows for the color coding
- Program the floweaver Sankey by adapting the .ipynb template and link it to the validated 1_F flow data xlsx template
    - Choose suitable colors and flow aggregations
    - Optional: Create several Sankey versions for the same dataset

**„Online“ part:**
- List all Sankey configurations in the SANKEY_LINK__ string (attribute reserve1 on the Cover sheet of the template)
- Upload the 1_F template to the IEDC via the IEDC team
- Convert the .ipynb to .py and the color pallette to .json and compile the floweaver .json configuration (command line)
- Upload the floweaver .json to the IEDC web server -> The Sankeys can now be generated in the web browser!

**Documentation part:**
- Switch the material, time, region, etc. labels in the .ipynb so that it works with the xlsx dataset downloaded from the IEDC
- Copy the modified .ipynb, the .py Sankey configuration, and the .json pallette to the IEDC-floweaver GitHub repo, commit
