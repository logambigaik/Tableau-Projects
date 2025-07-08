# Getting Started with Tableau Public and NYC Tree Census Data

## Step 1: Download the Data

1. Visit the GitHub repository containing the datasets for this course.
2. Click on the green **"Code"** button.
3. From the drop-down menu, select **"Download ZIP"** at the bottom.

> ![Download ZIP](Image showing green "Code" button and "Download ZIP" option highlighted)

4. Once downloaded, extract the ZIP file and move the **datasets** folder to a location outside the ZIP archive.
5. Tableau cannot access data inside a ZIP file, so it must be unzipped first.

---

## Step 2: Open the Dataset in Tableau Public

1. Open **Tableau Public**.
2. Select the **"Text file"** option in the left pane.
3. Navigate to and open the file named:  
   `tree-census-NYC_2015.csv`

Once loaded, Tableau will display the **Data Viewer** screen:

- You can preview the data table.
- View metadata (field names).
- See other connected data sources.
- Join multiple data tables if needed.

---

## Step 3: Rename a Field for Clarity

1. Open the Data Dictionary:
   - Either open the `TreeCensus-2015_data-dictionary.PDF` file inside the datasets folder.
   - Or [click here](#) to view it online.

2. Locate the field `Tree Dbh` (which stands for trunk diameter at breast height, approximately 54in/137cm above ground).

3. Double-click the field name **Tree Dbh**.

4. Rename it to: **Trunk Diameter**

> Example:  
> - Left box: `Tree Dbh`  
> - Right box: `Trunk Diameter`  
> - A red arrow points from the old name to the new name.

---

## Step 4: Change the Data Type of a Field

In the **Metadata Pane**:

1. Locate the field named **Tree Id**.
2. Currently, it's interpreted as numerical (indicated by `#`).
3. Click on the `#` symbol under the “Type” column for **Tree Id**.
4. Select **String**.

> Once changed, Tableau will show `Abc` instead of `#`, indicating that it's now a text/categorical field.

> ![Change Data Type](Image showing "Abc" in the "Type" column next to "Tree Id")

---

#### After change:

<img src="https://github.com/user-attachments/assets/c0de3170-9936-4167-85b0-6a5cc7d0d5dd" width=300><br>

<img src="https://github.com/user-attachments/assets/6245678f-eff6-4c85-902a-246a30b0ef69" width=600


