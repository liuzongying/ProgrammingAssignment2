    Programming week 4  Assignment1
    ======================


    best <- function(state, outcome) {
      ## Read outcome data
      ## Check that state and outcome are valid
      ## Return hospital name in that state with lowest 30-day death
      ## rate
    hospital<-data.frame()
    name<-data.frame()
    data<-data.frame()
        
    hospital<-read.csv(file='outcome-of-care-measures.csv', header = T,na.strings="Not Available")
    validoutcome<-c('heart attack','heart failure','pneumonia')
    
    if(!outcome %in% validoutcome){
       stop('invalid outcome')
    }
      name<-unique(hospital[,7])
      if(!state %in% unique(name)) {
       stop('invalid state')
    }
         

         colnames(hospital)[13]='heart attack'
         
         colnames(hospital)[17]='heart failure'
        
         colnames(hospital)[23]='pneumonia'

         data<-hospital[hospital$State==state,]

         
         data<-hospital[hospital$State==state,c('Hospital.Name',outcome)]
         data1<-data[complete.cases(data),]
         num<-min(data1[,2])
         result<-data1[data1[,2]==num,c('Hospital.Name')]
         as.character(result)

     
         #min <- which.min(data[,outcome])
         #result<-data[min,"Hospital.Name"]
         #as.character(result)
  }      
