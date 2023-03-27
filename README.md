# UFOs
Module 12, JavaScript - UNCCH Data Analytics Bootcamp, Spring 2023

## Project Overview

### Purpose
In this exercise, a webpage with a dynamic table was created to assist Dana, a data journalist who is interested in understanding UFO sightings. This webpage will also contain her article and headline, and feature text-box inputs to allow readers to filter the table data. Filters for the UFO sightings include options for the city, state, country, and shape of the object. 


## Method
The source data is stored in a JavaScript array, named data.js
Using html, JavaScript (inlcuding Bootstrap), and css, a fully-functional interactive webpage was created to offer a table-based data visualizaion. Filter boxes were created in the index.html file as list elements, with examples displayed in each text box to help promt the viewer to input filter selections as text strings. The app.js file was modified to store any filter search entries as an array, then that array called upon in a funtion that loops through each row item the the table to display only results that meet the selected filter search criteria.  

A sample function employed within app.js to capture the current filter information used to update the data table is as follows: 
```
function updateFilters() {
  // 4a. Save the element that was changed as a variable.
  let changedElement = d3.select(this);
  // 4b. Save the value that was changed as a variable.
  let elementValue = changedElement.property("value");
  console.log(elementValue);
  // 4c. Save the id of the filter that was changed as a variable.
  let filterId = changedElement.attr("id");
  console.log(filterId);
  
  // 5. If a filter value was entered then add that filterId and value
  // to the filters list. Otherwise, clear that filter from the filters object.
  if (elementValue){
    filters[filterId] = elementValue;
  } else {
    delete filters[filterId];
  }

  // 6. Call function to apply all filters and rebuild the table
  filterTable();
}
```

Sample code used to loop through the user-applied filters to determine matches was partly derived from a solution found here: https://stackoverflow.com/questions/68230024/filter-javascript-array-based-on-multiple-values
...and is displayed as follows: 
```
    // 9. Loop through all of the filters and keep any data that matches the filter values
    filteredData = filteredData.filter((elementValue) => {
        for(i in filters) {
            if(elementValue[i] !== filters[i]) {
            return false;
            }
        }
        return true;
    }); 
```

## Results
The webpage displays by default the entire dataset in its table. To find desired sightings in a particular city, state, country, or of a certain shape, enter this information into the appropriate text boxes located left of the data table.  

- Webpage without any filters selected:

    ![UFOsite_blank_filters](/UFOsite_blank_filters.png)

   
- Webpage with filters for state of Oregon and country of US selected:

    ![UFOsite_or&us_filters](/UFOsite_or&us_filters.png)


- Webpage with filters for city of El Cajon, state of California, country of US, and shape of Triangle selected:

    ![UFOsite_elcajon&ca&us&triangle_filters](/UFOsite_elcajon&ca&us&triangle_filters.png)

- Observations: 
    - California leads the way in UFO sightings by state, followed by Florida. 
    - Canada only had two UFO sightings in the supplied dataset.
    - The reported shapes of UFOs are quite varied.
    
## Summary
A drawback of this updated webpage design is that the text input boxes do not limit viewer's choices to available options. This could lead to a user experiencing a false-negative when selecting a filter due to a misspelling, capitalization, or other type of error. 

- Additional recommendations for further development include:
    - Ideally, the filter boxes would be drop-down selectors instead of empty text fields, which would limit search options to available filter criteria and therefore avoid errors of misspelling, etc. 
    - Options for sorting the table could be helpful to the viewer, such as a button used to sort the displayed data by Date or Duration, either in ascending or descending order.