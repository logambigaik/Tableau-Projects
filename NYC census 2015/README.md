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

<img src="https://github.com/user-attachments/assets/c0de3170-9936-4167-85b0-6a5cc7d0d5dd" width=400>
<br>
<img src="https://github.com/user-attachments/assets/eec23d85-5a25-45b8-91ab-e11746de1864" width=600>

#### Joins, Unions, and Relationships
• Let’s say we wanted to be able to show whether trees are native species or not. If we just so happen to have a dataset with each tree’s Latin name and its native species status, we can do just that! All we have to do in Tableau is ensure that the two tables form a Relationship based on their shared column.

<img src="https://github.com/user-attachments/assets/8cb9aef9-8b31-49ae-a392-63980d84a362" width=440>


# Joining Datasets in Tableau Public

## Step 1: Open the Data Source Tab

- Make sure the **Data Source** tab (bottom-left of your screen) is selected.
  
> ✅ There are four buttons. From left to right:  
> - **Data Source** (selected)  
> - **Sheet1**  
> - Three icon buttons
<img src="https://github.com/user-attachments/assets/b6d6fb99-6056-479b-aeb1-3fcc80b893c9" width=400> <br>
<img src="https://github.com/user-attachments/assets/eb0bcd7f-9ebf-4653-ba48-85433ec3a01c" width=400>

---

## Step 2: View Your Data Connections

- The **tree-census-NYC_2015.csv** file should already be loaded.
- On the left pane, you’ll see a list of files from the same **datasets** folder.

### Look for:
- **Connections** → Shows the current CSV connected (e.g. `tree-census-NYC_2015`)
- **Files** → A list of available files, such as:
  - `FFA-wildlife-strikes.csv`
  - `income-NYC_2015.csv`
  - `passenger-counts_2014.csv`
  - _and more_

---

## Step 3: Add a New File to the Relationship

1. Find **tree_species_nyc.csv** in the list of files.
2. **Drag and drop** it next to the `tree-census-NYC_2015.csv` file on the **Relationships Panel**.

> 🧠 You will see an orange "noodle" indicating a potential relationship between the files.

<img src="https://github.com/user-attachments/assets/389b421b-f57a-44c7-9b20-6db908624717" width=400>


---

## Step 4: Resolve the Field Matching Error

After dropping, Tableau may show an **error**:

- You'll see two boxes connected by a red **dashed line**.
- A red triangle with an **exclamation mark** appears between them.

> 🔺 This means Tableau doesn’t know how to match fields between the datasets — they don’t share a column with the same name.

---

## Step 5: Define the Relationship Manually

1. Go to the **Select a field** section (bottom-left of your Tableau window).
2. You’ll see three sections:
   - **Left file** → `tree-census-NYC_2015.csv`
   - **Operator** → default is `=`
   - **Right file** → `tree_species_nyc.csv`

3. In the **left drop-down**, choose:  
   ➤ `Spc Latin`

4. In the **right drop-down**, choose:  
   ➤ `Scientific name`

> ✅ Once selected, the error disappears, and the red dashed line turns into a solid **orange line**.

<img src="https://github.com/user-attachments/assets/0ad85514-c138-4e30-b51e-9debc0ebe7d3" width=400>


---

## Success!

- You've successfully joined both datasets based on matching species fields!
- You can now explore **combined data** from:
  - `tree-census-NYC_2015.csv`
  - `tree_species_nyc.csv`

> 🌳 Enjoy your analysis with enhanced tree species information!


# Understanding Aggregates in Tableau with Tree Census Data

## Common Aggregates

| Aggregate | Description                          | Example                          |
|-----------|------------------------------------|---------------------------------|
| `SUM()`   | Adds all values in a field          | `SUM(Trunk Diameter) = 7,712,983 inches`  |
| `AVG()`   | Calculates the average (mean)       | `AVG(Trunk Diameter) = 11.28 inches`      |
| `MEDIAN()`| Finds the median (middle value)     | `MEDIAN(Trunk Diameter) = 9.0 inches`     |
| `COUNT()` | Counts number of items in a field   | `COUNT(Trunk Diameter) = 683,788 trees`   |
| `COUNTD()`| Counts distinct/unique items        | `COUNTD(Trunk Diameter) = 146 unique measurements` |

<img src="https://github.com/user-attachments/assets/af357a7c-139d-4379-81e0-812f9fe74b32" width=400>

---

## Which Zip Code Has the Biggest Tree Trunks?

### Step 1: Sum of Trunk Diameters by Zipcode

- Drag **Zipcode** to Rows shelf.
- Drag **Trunk Diameter** to Columns shelf (default aggregation is SUM).

**Note:**  
- This shows the sum of all tree trunk diameters by Zipcode.
- Larger sums often reflect more trees, not necessarily bigger trunks.

---

### Step 2: Average Trunk Diameter by Zipcode

- Change aggregation of **Trunk Diameter** pill from `SUM()` to `AVG()`:
  - Hover over the pill → dropdown arrow → **Measure** → **Average**.
  
This shows the **average trunk diameter**, giving a better measure of which zip code has bigger trunks on average.
<img src="https://github.com/user-attachments/assets/a7d4a99b-5fdc-478c-bbd2-9f73bbdb7ee7" width=400>

<b>Tick - SHow Label to display the average values of Trunk diameter</b>
<img src="https://github.com/user-attachments/assets/c3b9e3af-2c7e-492f-a94a-a058e6a678d0" width=400>

---

### Step 3: Count of Trees by Zipcode

- Drag **Tree ID** to Columns shelf.
- Change its aggregation to **COUNTD()** (Count Distinct):
  - Click dropdown on Tree ID pill → **Measure** → **Count Distinct**.

This counts distinct trees per zip code, helping verify if sums correspond to tree counts.

<img src="https://github.com/user-attachments/assets/5b5e10ec-474b-4d86-bb0f-efc77100b4b0" width=400><br>

<img src="https://github.com/user-attachments/assets/336e4560-4d0a-4fe3-be05-c179b30ccb85" width=400> <br>

---

## Example Chart Setup in Tableau

1. **Open Tableau** and connect to `tree-census-NYC_2015.csv`.
2. Open a new workbook.
3. Drag **Trunk Diameter** to Rows shelf.
4. Drag **Boroname** (borough names) to Columns shelf.
5. Click the **Swap Rows and Columns** button (curved double-arrow icon).
6. Drag a copy of **Boroname** to the **Color** shelf (hold CTRL or Command while dragging).

### Adjust Aggregation

- The default aggregation is `SUM(Trunk Diameter)`.
- Change it to `AVG(Trunk Diameter)` by clicking the pill dropdown → **Measure** → **Average**.
- Drag the **AVG(Trunk Diameter)** pill to the **Label** shelf (hold CTRL/Command to copy).
- Sort the **Boroname** field in **Rows**:
  - Click dropdown on Boroname → **Sort**.
  - Sort by **Field** → Aggregation: **Average** → Order: **Descending**.

<img src="https://github.com/user-attachments/assets/d4e0235e-4cca-4a76-8dc8-1c8830d243e6" width=400>

---

## Observations from the Borough Data

- Queens has the highest average trunk diameter (~12.6 inches).
- Queens also has the highest sum of trunk diameters but by a wider margin.
- To check tree counts by borough:
  - Remove **Trunk Diameter** from Columns and Label shelves.
  - Drag **Tree ID** to Columns.
  - Change aggregation of Tree ID to **Count Distinct** (`COUNTD`).
  - Optionally, drag **COUNTD(Tree ID)** to Label shelf.

---

## Percent of Total Trees by Borough

- Click dropdown on **COUNTD(Tree ID)** pill → **Quick Table Calculation** → **Percent of Total**.
- Remove and re-add the pill to Label shelf to update labels accordingly.

<img src="https://github.com/user-attachments/assets/ed49a2ba-98e5-4714-a59d-e23d4f9368be" width=400>

---

# Filtering in Tableau: Improving Performance and User Experience

When working with large datasets, Tableau’s filter function is essential to improve performance, reduce wait times, and focus on relevant data. Filtering also helps remove null values or extraneous data points.

---

## Why Use Filters?

- Avoid the "rainbow spinning wheel of death" caused by heavy data processing.
- Improve dashboard performance by reducing the number of marks Tableau redraws when interacting with visualizations.
- Filter before plotting individual data points (e.g., in maps or scatterplots) to speed up rendering.

---

## Step-by-Step Filtering Example

### 1. Filter the "Count D" Visualization

- Open your Tableau workbook and find the **“Count D”** visualization.
- This chart shows the distinct count of Tree ID (`CNTD(TreeID)`) by **Boroname** (borough).
- Drag the **Health** field to the **Filters Shelf**.
- In the filter dialog, select only **Good** health status.
- This filter restricts the visualization to trees in good health only.

<img src="" width=400>
---

### 2. Create a Map to Visualize Tree Locations with Filters

- Open a new worksheet and name it **“Tree Locations”**.
- Double-click **Longitude** (goes to Columns shelf) and **Latitude** (goes to Rows shelf).
- Tableau will plot a single point representing the average location of all trees.
- To show each tree as a separate point:
  - Drag **Tree ID** to the **Detail** shelf.
  - When prompted, choose **Add all members** (this may take some time).

---

### 3. Improve Map Performance with Filters

- Before adding Tree ID to Detail, filter data to reduce marks:
  - Drag **Boroname** to the **Filters Shelf**.
  - Select only one borough, e.g., **Bronx**.
- This reduces the number of data points from ~700,000 to ~85,000, speeding up map rendering.
- Now add **Tree ID** to the Detail shelf.
- Drag **Health** to the **Color** shelf to color-code tree health status.

---

### 4. Make the Map More Readable

- In the **Marks** card, click **Size**.
- Drag the size slider all the way to the left to reduce point size.
- Smaller points make the map clearer and help reveal minority data points that might be hidden under larger points.

---

### 5. Additional Performance Tips

- If performance is still slow, filter by specific **Zip Codes** (instead of the whole borough) to reduce data points further.
- To allow dashboard users to change filters dynamically:
  - Click the dropdown arrow on the **Boroname** pill in the Filters shelf.
  - Select **Show Filter**.
  - This adds a filter control (checkbox list) to the view, enabling user interaction.

---


https://public.tableau.com/views/NYC-census-data-2015/Dashboard1?:language=en-GB&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link



