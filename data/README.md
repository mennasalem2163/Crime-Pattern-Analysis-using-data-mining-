# Data setup

Raw datasets are not bundled. The notebook combines Los Angeles incident records with seven community health profile theme tables.

## File references found in the notebook

- `/content/CSV CHP Theme 1 - Demographics - Data.csv`
- `/content/CSV CHP Theme 11 - Healthcare Access - Data.csv`
- `/content/CSV CHP Theme 2 - Social Determinants of Health - Data.csv`
- `/content/CSV CHP Theme 3 - Physical Activity and Nutrition - Data.csv`
- `/content/CSV CHP Theme 5 - Housing and Health - Data.csv`
- `/content/Crime_Data_from_2020_to_Present 2.csv`
- `/content/Excel CHP Theme 6 - Community Safety - Metadata and Data.csv`
- `/content/Excel CHP Theme 9 - Behavioral Health - Metadata and Data.csv`
- `/content/Merged_Crime_Data_LA.csv.crdownload`
- `Crime_Data_with_Neighborhoods.csv`
- `la_crime_data (3).csv`

The notebook also loads the merged table through `dataset_path`, currently `/content/drive/MyDrive/Merged_Crime_Data_LA.csv`. Update it to your location.

The crime input is referenced with more than one filename. Point both loading cells to your actual input file. The merge stage writes `la_crime_data.csv`, while a later cell reads `la_crime_data (3).csv`; reconcile these names before running. Inspect all reads and writes before a full execution.

Record the source URLs, download dates, data versions, and applicable terms when obtaining the original files. Source URLs were not verified during packaging.
