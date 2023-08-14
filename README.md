# SFC
# Here is my python code to print a Space Filling Curve .

def rotate_1(l):
    for i in l :
        x,y = i
        ans_list_1.append((y,x))

def shift_1 (l,n):
    for i in l :
        x,y = i
        ans_list_1.append((x+(2**(n-1)),y))

def shift_2 (l,n):
    for i in l :
        x,y = i
        ans_list_1.append((x+(2**(n-1)),y+(2**(n-1))))

def rotate_2(l,n):
    '''
    for i in l:
        x,y = i 
        if (x==y):
            k = 2**(n-1)+1-x
            ans_list_1.append((k,k+2**(n-1)))
        else :
            ans_list_1.append((x,y+2**(n-1)))
    '''
    for i in range(4**(n-1)-1,-1,-1):
        x,y = l[i]
        y = 2**n -(y-1)
        ans_list_1.append((x,y))

def SFC(n):
    global ans_list_1,l
    j = 1 
    while j!=n+1:
        rotate_1(l)
        if (j==1):
            j+=1
        if (n==1):
            print(ans_list_1)
            return None
        shift_1(l,j)
        shift_2(l,j)
        rotate_2(ans_list_1,j)
        l = ans_list_1
        if(j!=n):
            ans_list_1=[]
        j+=1
    print(ans_list_1)


l =[(1,1),(2,1),(2,2),(1,2)]
ans_list_1,ans_list_2 = [],[]

print("\n\n # Space Filling Curve # \n")
n = int(input("Enter the number of rows :"))
print("\n")
SFC(n)
