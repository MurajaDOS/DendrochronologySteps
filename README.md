# DendrochronologySteps
Dendrochronology Analysis

- If you use my code for your analysis, please don't forget to refer to this project in your work, I really appreciate it :)

Data:
CANELA RWI - Will be available soon at the Tree-Ring Data Bank (ITRDB), wait for updates. For now, you can try to use your own .tucson file obtained from CDENDRO. Be careful with naming your files, here we use the pattern ACA01a, where A = species Araucaria, CA = City/Location, 01 = tree number, and a = sample of the tree. Follow this pattern or create your own and modify the code when working with tree indices (in DecStat script).

SUNSPOT INDEX - You can obtain it here: https://www.sidc.be/SILSO/datafiles. Pay attention to which kind of analysis you are doing. Analysis by semester, seasonal, and annual, may need some additional procedures, or you need to format the data in the same shape as the example here.

PREC, TEMPMAX, TEMPMED, TEMPMIN - These are the climatic series for the region you are analyzing. For Brazil, you can obtain climatic data at the INMET website. PREC = Precipitation; TEMPMAX = Maximum Temperature; TEMMED = Mean Temperature; TEMPMIN = Minimum Temperature.

TIPS:
- Make sure you have all the packages necessary installed and loaded. For further questions, you can also check the package documentation just by searching it on Google.
- Remember to plot the graphics of the analysis you want. If you run the full code at once, the graphics will be only for your annual analysis. e.g. Run the first Chunk for monthly correlation and then run the graphic Chunk.
- It is very important to check the function documentation to make sure you are using it correctly and for the correct analysis.

Scripts Description:

- "DecStat.Rmd" reads the .tucson file, provides all the relevant statistics for the tree ring series, can work with samples or transform them into tree indices, perform 3 methods of detrending (SPL, NEGEXP, and RCS), and will generate the Mean Chronology (Ring Width Index) and also calculate the important statistics.

- "CORR_Mon-Sea-Sem-Ann.Rmd" performs monthly, seasonal, semester, and annual correlation between a climatic time series and the RWI. Pearson's correlation will provide the linear relationship between the two time series. It generates graphics of the correlation results.

- "PartialCorrSeason_Mon-Sea.Rmd" is the correlation between one time series (here is precipitation) and the RWI, excluding the variation caused by a third time series (here is TEMPMAX, or TEMPMED, or TEMPMIN) on the first time series (precipitation). It generates graphics of the correlation results.

- "TimeSeriesWaveletsTransf.Rmd" performs the wavelet transform for each of the time series that will be analyzed. In the code, the Canela RWI and the SUNSPOT data are used. It generates the wavelet.list that contains all the information about the transformation and will be used as .rds to be opened in the Cross Wavelet Analysis. It also generates the wavelet transform graphic with the time series on the top. The function is set to give the best cone of influence (COI) and the 95% significant areas within the black contours. These parameters can be changed by adding more parameters (check the library documentation).

- "CrossWaveletsAnalysis.Rmd" here the data from the Wavelet Transformation (.rds) will be loaded and the Cross Wavelet Coherence is performed. The function is set to give the best cone of influence (COI) and the 95% significant areas within the black contours. These parameters can be changed by adding more parameters (check the library documentation). It also generates the cross wavelet coherence graphic with the two time series on the top. Arrows in white represent the phase of the relationship between the two time series (here Canela RWI and SUNSPOT), if pointing to the right they are in phase, if left they are in anti-phase. It saves a .csv file containing the Averaged Power of the Cross Wavelet Coherence.

- "Power_Wavelet.Rmd" calculates the Cross Wavelet Average Power by using a .csv file generated in the Cross Wavelet Script. The SUNSPOT INDEX (is being used with Canela RWI (.tucson).
