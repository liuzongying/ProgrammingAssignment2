    #week 2 Assignment01
    #======================

    #couraera R programming(rprog-017) complete assignment 2


     complete <- function(directory, id = 1:332) {
        ## 'directory' 是长度为1的字符向量，指明
        ##  CSV 文件的位置

        ## 'id' 是正整数向量，指明监测点的ID号，
        ## 将要被使用的
        
        ## 返回以下格式的数据帧：
        ## id nobs
        ## 1  117
        ## 2  1041
        ## ...
        ## 其中'id' 是监测点ID编号，而'nobs'是
        ## 完整案例的数量
        
     result<-data.frame()
        for(file in rep(id)){
            completedata<-read.table(paste(directory,'/',sprintf('%03d',file),'.csv',sep=''),sep=",",header=TRUE)

            nobs1<-nrow(completedata[complete.cases(completedata),])
                      
            result<-rbind(result,cbind(file,nobs1))
       }
    colnames(result)<-c('id','nobs')
    result
    }
