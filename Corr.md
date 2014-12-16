   #Week 2 Assignment Corr
   #======================

   #couraera R programming(rprog-017) Week 2 assignment corr
   
      corr <- function(directory, threshold = 0) {
        ## 'directory' 是长度为1的字符向量，指明
        ##  CSV 文件的位置

        ## 'threshold' 是长度为1的数值向量，指明
        ## 完整观测的案例的数量 (针对所有
        ## 变量) 是必须的，为了计算这两个的相关性：
        ## 硝酸盐(nitrate)和硫酸盐(sulfate); 默认值为 0

        ## 返回相关性的数值向量
      result<-numeric()
      num<-data.frame()
      data<-data.frame()
     # threshold<-numeric()
      id<-1:332
      for(file in rep(id)){
           data<-read.table(paste(directory,'/',sprintf('%03d',file),'.csv',sep=''),sep=",",header=TRUE)
           rownumber<-nrow(data[complete.cases(data), ])
         
           num<-rbind(data,data[complete.cases(data),])
           if(rownumber>threshold){
           result<-c(result,cor(num['nitrate'],num['sulfate'],use='pairwise'))
          }
          }
      print(result)
     }
