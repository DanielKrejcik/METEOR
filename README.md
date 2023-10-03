# METEOR
Final project @ WBS Coding School | A predicitive model of renewable electricity generation | collaborative project with Federico Naracci

This final project was meant to bring together the skills acquired during the 12 weeks of bootcamp. Having a personal interest in the energy supply transition and the volatility of renewable electricity generation we decided to work on a model to predict the electricity generation based on weather conditions.
Thanks to the German renewable funding scheme (EEG) much of the desired data to work with is publicly available. In order to reduce the project's overall complexity we settled with one of the four German transmission grid areas - 50 Hertz - which covers the east of the country as well as the city state of Hamburg.

The notebooks found in this repository show the following steps:
  1. Extracting generation facilities:
  The datasets containing information on generation facilities provided by Marktstammdatenregister (link #1 below) and Bundesnetzagentur (see link #2) cover the area of Germany, so the facilities under scrutiny have to be extracted.
  2. Generation data cleaning/preparation:
  Not all the information provided by the datasets was necessary for our purposes so these data was removed, additionally some harmonizing and the addition of missing geo-data was performed.
  3. Clustering facilities around weather stations:
  When trying to model depending on weather conditions, weather data is necessary. Therefore the facilities were clustered around weather stations by minimal distance and each facility got one assigned weather station. The weather stations and according weather data was taken from the datasets provided by Deutscher Wetterdienst (link below). Note: The extraction and condensation of the weather data and the relevant stations is not shown in this repository. 
  4. Assigning generation numbers per facility:
  The available data on the yearly generation per facilty (see link #3) was added in the newly generated dataframes. Additionally visualising the clusters using plotly.
  5. Weighting facilities and clusters:
  Since the generation numbers per facility are only available on a yearly basis (see link #3), the (hourly - granularity of the weatherdata) generation numbers per facility and cluster have to be estimated. Therefore the weight per facility/cluster in the total genaration is calculated. The reason for that is the availability of real time generation data when it comes to the whole area under scrutiny. Two approaches: weighted by a) capacity and by b) yearly generation
  6. Assigning generation numbers per cluster:
  Using the estimations to create hourly generation numbers to be in line with the weather data.
  7. Calculating the predictions
  Using LightGradientBoostingRegressor to predict the hourly generation numbers - based on both estimations from before.
  8. Visualising the prediciton:
  Comparing the predictions, the official prediciton and the acutal generation (see link #5), showing that the generation based estimation worked better and visualising those using plotly.

#1: https://www.marktstammdatenregister.de/MaStR/Datendownload
#2: https://www.bundesnetzagentur.de/DE/Sachgebiete/ElektrizitaetundGas/Unternehmen_Institutionen/Versorgungssicherheit/Erzeugungskapazitaeten/Kraftwerksliste/kraftwerksliste-node.html
#3: https://www.netztransparenz.de/de-de/Erneuerbare-Energien-und-Umlagen/EEG/EEG-Abrechnung/EEG-Jahresabrechnungen/EEG-Jahresabrechnungen-2022-2000
#4: https://opendata.dwd.de/climate_environment/CDC/observations_germany/climate/hourly/
#5: https://www.smard.de/home/downloadcenter/download-marktdaten/
