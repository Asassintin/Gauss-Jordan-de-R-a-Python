# Codigo R  a Python

a=c(2,4,6,18,4,5,6,24,3,1,-2,4)
a

#A=matrix(a,3,4) #acomodo por renglon default
A = matrix(a,nrow=3,ncol=4, byrow=TRUE) #or FALSE
A


A[2,4] #un solo elemento de la matriz A (a24)
A[,1] #muestra columna 1
A[3,] # muestra renglo

#columna 1
A[1,]=(1/A[1,1])*A[1,] #R1 uno (R1=(1/2)R1)
A

A[2,]=-A[2,1]*A[1,]+A[2,] #R2 ceros R2=R2+(-4)R1
A

A[3,]=-A[3,1]*A[1,]+A[3,] #R3 ceros R3=R3+(-3)R1
A

#columna 2
A[2,]=(1/A[2,2])*A[2,] #R2 uno (normalizar) R2=(-1/3)R2
A

A[1,]=-A[1,2]*A[2,]+A[1,] #R1 ceros. R1=(-2)R2+R1
A

A[3,]=-A[3,2]*A[2,]+A[3,] #R3 ceros
A

#columna 3
A[3,]=(1/A[3,3])*A[3,] #R3 uno
A

A[1,]=-A[1,3]*A[3,]+A[1,] #R1 ceros
A

A[2,]=-A[2,3]*A[3,]+A[2,] #R2 ceros
A

sol = c(A[1,4], A[2,4], A[3,4])
sol   

print("la solucion es (x1,x2,x3)="); print(sol)
