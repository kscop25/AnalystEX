# RISI Data Analyst Candidate Exercise
## Overview
The intention of this exercise is to assess your ability to think critically and apply your technical skill set to an analytics problem designed to reflect some of the tasks you are likely to encounter as a Data Analyst at RISI, albeit in a simplified manner. This exercise is deliberately vague and no specific approach or answer is “right”. However, we are particularly interested in seeing code that is efficient and clear.

### Instructions
- Using R, download the (Rural Atlas)[https://www.ers.usda.gov/data-products/atlas-of-rural-and-small-town-america/] data.
- Load all available sheets into your R session. 
   - Note that the Rural Atlas .CSV files are a mix of comma and tab separated sheets
- Clean the variable names for each data set to snake_case (all lowercase, words separated by single underscores)
- Using R, create a new folder called 'clean_data'
- Write the cleaned data out to your new folder. The output file names should also be in snake_case.
- Download the 2018 (Census County Cartographic Boundary files)[https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html] and unzip it using R. Use the 500K resolution file.
- Using R, Python, or QGIS, map the rural counties of New England. Use the 2013 Non-Metro rural designation from the Rural Atlas. Choose and include in your map 2 or more variables from the Rural Atlas that interest you

### Required steps:
- Clone this Github repository.
- Download and clean the data sets
- Create a map
- Commit all code and output to the repository

### Deliverable: 
- Any code and documentation required to reproduce your analysis and its results, including scripts, readmes, diagrams, or other instructive material provided via a link to a Github repository.
- A map as described above.

## Guidelines
We should be able to duplicate your results with whatever code and documentation you provide and nothing else. Overly documented code is something we never complain about! For the mapping component of this exercise, polish and aesthetics are important. For the data download and processing, concision and clarity are most important. Note that, excluding comments and blank lines, it is fully possible to do all of the download and processing in fewer than 20 lines of code.

With that said, this task will take some time. If you need more time or cannot complete all components of the exercise please contact us and we can make accommodations; certain skills may be more important to demonstrate than others based on experience.

### Dos
1. Do ask questions!
2. Do use code efficiently and comment clearly
3. Do review your work and minimize the occurrence of errors
4. Do include checks and data diagnostics within your code.
5. Do use scripts whenever possible

### Don’ts
1.  Don’t use spreadsheets in this exercise; doing tabulations in a spreadsheet is fine but no part of your analysis should rely on them.
2.  Don’t rely heavily, if at all, on GUI commands or instructions. We want to see how you program, not how well you use a particular software package. 
3.  Don’t assume we know what you’re doing; document it.
4.  Don’t be afraid to think outside the box. You are encouraged to augment your analysis with something that demonstrates your unique toolkit but it must clearly provide value or insight
