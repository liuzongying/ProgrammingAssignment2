   #week 2 Assignment pollutantmean
   #======================

   #couraera R programming(rprog-017) week2 assignment pollutantmean
   
   
    pollutantmean <- function(directory, pollutant, id = 1:332) {
   # 'directory' is a character vector of length 1 indicating
   
   # the location of the CSV files
  
   # 'pollutant' is a character vector of length 1 indicating
   
   # the name of the pollutant for which we will calculate the mean; either "sulfate" or "nitrate".
  
   # 'id' is an integer vector indicating the monitor ID numbers to be used
  
   # Return the mean of the pollutant across all monitors list
   # in the 'id' vector (ignoring NA values)
 
    pollutantdata<-data.frame()
    for(file in rep(id)){
        pollutantdata<-rbind(pollutantdata,read.table(paste(directory,'/',sprintf('%03d',file),'.csv',sep=''),sep=',',header=TRUE))
    }
    mean(as.matrix(pollutantdata[pollutant]),na.rm=TRUE)
 }


