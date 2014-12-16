ProgrammingAssignment2
======================

couraera R programming(rprog-017) programming assignment 2
  makeCacheMatrix <- function(x = matrix()) {
  s <- NULL
  set <- function(y) {
    x <<- y
    s <<- NULL
  }
  get <- function() x
  setsolve <- function(solve) s <<- solve
  getsolve <- function() s
  list(set = set, get = get,
         setsolve = setsolve,
         getsolve = getsolve)
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
