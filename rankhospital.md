   Programming week 4 Assignment1
    ======================

    rankhospital <- function(state, outcome, num ) {
      
      ## Read outcome data
      ## Check that state and outcome are valid
      ## Return hospital name in that state with the given rank
      ## 30-day death rate
    hospital<-data.frame()
    name<-data.frame()
    data<-data.frame()
        
    hospital<-read.csv(file='outcome-of-care-measures.csv', header = T,na.strings="Not Available")
    #打开时把not available设置成na，便于以后处理数据
    validoutcome<-c('heart attack','heart failure','pneumonia')
    
    if(!outcome %in% validoutcome){
    #‘%in%’用于查看有没有变量从在向量里   
        stop('invalid outcome')
    }
      name<-unique(hospital[,7])
      if(!state %in% unique(name)) {
      #unique()用于把重复的变成一个
         stop('invalid state')
    }
         

         colnames(hospital)[11]='heart attack'
         
         colnames(hospital)[17]='heart failure'
        
         colnames(hospital)[23]='pneumonia'

         
         data<-hospital[hospital$State==state,c('Hospital.Name',outcome)]
         data1<-data[complete.cases(data),] #把na都去掉，保留全部有用的数据
         data2<-data1[order(data1[,2]),]    #把data1的第二列排序（从小到大）
         colnames(data2)[2]='Rate'
         data2<-data2[order(data2$Rate,data2["Hospital.Name"]), ]#把data2中Rate和hospital.name同事排序（优先Rate，name按字母顺序）
         n<-nrow(data2)
         data3<-cbind(data2,1:n)
         colnames(data3)[3]='Rank'  #整理过后de表（data3）
         if (num=='best'){num=1}
         if(num=='worst'){num=n}
         as.character(data3[num,1])
         #或可以写成as.character(data3[num,'Hosptial.name'])
         

     
                
}
