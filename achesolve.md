  #ProgrammingAssignment2
  #======================

  #couraera R programming(rprog-017) programming assignment 2

  makeVector <- function(x = matrix()) {
  # 函数内部定义的变量
  m <- NULL

  # 用来赋值的函数。"<<-" 是全局赋值符号。
  # 一般的赋值（"＝" 或者 "<-"）只会在当前函数内部（局部）对符号赋值；
  # 如果符号不存在，则创建新的符号。
  # 而 "<<-" 会搜索全局的符号进行赋值，
  # 所以此函数会把 y 的值赋给 makeVector 的输入变量 x，
  # 而不是在 set 函数内部创建一个新的符号 x，将 m 设为 NULL。
  set <- function(y) {
    x <<- y
    m <<- NULL
  }

  # 常值函数，返回 x，即需要处理的数据。
  get <- function() x

  # 将 mean 的值赋给 m，即缓存处理之后的结果。
  setmean <- function(mean) m <<- mean

  # 常值函数，返回 m，即处理结果。
  getmean <- function() m

  # 函数 makeVector 返回的是一个 list，其中共有四个元素，
  # 每个元素都是之前定义过的一个函数。
  list(set = set,
       get = get,
       setmean = setmean,
       getmean = getmean) 
}


    #above function create a matrix as makeCacheMatrix that be used in following matrix that has been done inverse matrix
    #set the first result of solve at memery of computer and save them as list




    cacheSolve <- function(x, ...) {
        m <- x$getsolve()
        if(!is.null(m)) {
                message("getting cached data")
                return(m)
        }
 
        data <- x$get()
        m <- solve(data, ...)
        x$setsolve(m)
        m

    #and then check whether the result to be memery of computer.
    #if result do not at memery, then do solve and set the result of solve in memery of computer
    #if result is at memery, then show 'getting cached data' and return result 
  

}


    #check result
    #cacheSolve(makeCacheMatrix(matrix(c(1,2,3,4,3,7,4,7,9),3,3)))
