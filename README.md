# sdmx-matrix-generator
This tool is used to visually model and design SDMX data artefacts, and generate the SDMX-ML markup for implementation. It is an enhancement of the Generic SDMX Design Matrix which has proven to be successful as a collaborative design tool for non-SDMX experts. 

The primary goal of the tool is to be able to create the artefacts without a lot of SDMX technical knowledge, and to put the focus on the statistical aspects of the data model. 

This tool maps to these GSBPM sub-processes:
  - 2.1 Design outputs (Dataflows design in Dataflows and DSD-Concept Matrix worksheets)
  - 2.2 Design variable descriptions (decomposition and creation of indicators in Indicator-Concept Matrix worksheet)
  - 3.1 Reuse or build collection instruments (generating SDMX-ML for reporting Dataflows)
  - 3.3 Reuse or build dissemination instruments (generating SDMX-ML for dissemination Dataflows)

To improve the tool, please request it by raising an issue and/or fork the repository and make the improvement yourself :)

Step-by-step guide (in the "How to use" worksheet of the generator tool)
0	Check and change the Parameters section on the "Generate SDMX-ML" worksheet, especially the folder paths		
1	Decompose existing Indicators into separate Concepts		
		If starting from an existing set of indicators, use the Indicator-Concept Matrix worksheet to list the indicators in column A, starting from row 3	
		Examine each indicator and decompose it into its atomic Concepts by doing the following steps:	
			Add new concepts in row 1, starting from column D if they do not exist
			Mark how the concept(s) are used for the indicator using the legend
			Include any extra breakdowns that are required for the indicators
2	Complete the Concept Scheme overview table with all concepts. 		
		Include the Concepts that were find in step 1	
		Use the SDMX Glossary for concept IDs and definitions	
		Commonly used concepts are already included, remove those that are not relevant.  	
		Complete the version, maintenance agency, and other details	
		To include several languages in the Concept Scheme name and descrption, copy the Name and Description cells in row 1, adding new cells at the end of the row. To indicate the languague, use this syntax in the fields: [Name: <language>] (follow the same convention as used for Name:en)	
		To include several languages for the Concepts, add Name:<language> and Description:<language> header cells in row 2. Then add the name and description values underneath their corresponding headers. Follow the same convention as used for Name and Descrption:en	
3	For each Code List identified in the Concept Scheme overview, copy the worksheet "New CL template" and rename it to CL_[your code list ID]		
		Use the Cross Domain Code Lists, Global Registry and other registries to reuse existing code lists	
		Ensure that the values in row 1 (Agency Id, Version, etc.) are entered. Ensure that the values are for the codelist, they may be different from the concept values (e.g. name)	
4	Populate each CL_[code list] worksheet with the code items		
		Pay attention to the coding guidelines	
		Check that the predefined code list worksheets (e.g. CL_CONF_STATUS) are up-to-date and correct	
		Cross Domain Code lists may need to be extended.  In this case they must change their maintenance agency from SDMX	
		CL_AREA is based on the full ISO 3166-1 alpha 2 classification.  Populate the CL_AREA worksheet with the required codes from that classification	
		Include integrity rules in the relevant column that can aid understanding of the codes	
5	Add the DSDs and their details to the DSDs worksheet		
		To include several languages for the DSD name and description, add Name:<language> and Description:<language> header cells in row 1. Then add the name and description values underneath their corresponding headers. Follow the same convention as used for Name and Descrption:en	
6	Add the Dataflows and their details to the Dataflows worksheet		
		To include several languages for the Dataflow name and description, add Name:<language> and Description:<language> header cells in row 1. Then add the name and description values underneath their corresponding headers. Follow the same convention as used for Name and Descrption:en	
7	Complete the DSD-Concept Matrix worksheet		
		Add the ownership organisations starting in row A6	
		Add the Dataflows in the corresponding column. Perhaps these can be derived from reporting tables or questionnaires.	
		In the matrix table, for each dataflow choose which concepts are used and how with the symbols in the Legend (e.g. # for any item is possible)	
			Use the legend symbols to indicate if all codes can be used (#), a subset (%), only one code (<the code>), or if the concept doesn't apply to the DSD (<blank>)
		Group the concepts into logical DSDs using criteria such as which data needs to travel together in the same message/DSD, which Datafows are closely related conceptually, which Dataflows share similar dimensionality	
			Use the dimension count column to determine if the number of dimensions in the DSD are acceptable
8	Create the constraints		
		Use the "Update Constraints from DSD Matrix" action on the "Generate SDMX & Params" worksheet to prefill the Constraint information in each Codelist worksheet	
		Look at each Dataflow in the DSD-Concept Matrix. For each cell that has a subset(%):	
			Go to the Concept's corresponding Code List. Find the Dataflow ID on the "Dataflows" row and the Concept ID underneath that cell (on the same line as "Concepts")
			Enter 1 for all codes that are valid (in the constraint) for this Dataflow/Concept
9	Generate  the SDMX-ML by batch or individual artefacts		
		Batch generate SDMX-ML for artefacts:	
			 Choose which artefacts to generate by changing the Generate? Column: 1=Generate
		Individually generate artefact SDMX-ML:	
			In DSDs and Dataflows worksheets, click the ID of the artefact to generate
			In Codelist worksheets, click the cell "GENERATE CODELIST!"

David Barraclough
