**1)linked file**
```cpp
#include <stdio.h>



struct file{
        char filename[10];
        int start,size,block[10];
}f[10];




void main(){
    int n,i,j;
        printf("Enter no of file\n");
        scanf("%d",&n);
        
 for(i = 0 ; i < n ; i++){
     printf("Enter filename\n");
    scanf("%s",f[i].filename);
    printf("Enter start of block\n");
    scanf("%d",&f[i].start);
    f[i].block[0]=f[i].start;
    printf("Enter no of block\n");
    scanf("%d",&f[i].size);
     printf("Enter the block numbers \n");
     for(j=1 ;j <= f[i].size ; j++ )
          scanf("%d",&f[i].block[j]);
    
        }
    
    printf("file\tstart\tsize\tblock\n");
    for(i=0 ; i<n ; i++){
        
        printf("%s\t%d\t%d\t",f[i].filename,f[i].start,f[i].size);
        for(j=1 ;j <=f[i].size-1 ; j++  )
            printf("%d-->",f[i].block[j]);
            printf("%d",f[i].block[j]);
            printf("\n");
        
        
        
    }
    
}
```
---------------------------------

**2)index file**

```cpp
#include<stdio.h>
void main(){
    
    int n,filename,start[20],size[20],m[20],block[20][20],i,j;
    
    
     printf("Enter no of file\n");
        scanf("%d",&n);
        
 for(i = 0 ; i < n ; i++){
    printf("Enter start of block\n");
    scanf("%d",&start[i]);
    printf("Enter size of file\n");
    scanf("%d",&size[i]);
    printf("Enter block accupied\n");
    scanf("%d",&m[i]);
     printf("Enter the block of file \n");
     for(j=0 ;j <m[i] ; j++ )
          scanf("%d",&block[i][j]);
          
        }

    
    printf("file\tindex\tlength\t");
    for(i=0 ; i<n ; i++){
        
        printf("\n%d\t%d\t%d\t",i+1,start[i],m[i]);
    }
    printf("\nenter filename\n");
    scanf("%d",&filename);
    printf("the file name %d",filename);
    i=filename -1;
    printf("\nthe index is %d\n",start[i]);
      printf("Enter block accupied is ");
            for(j=0 ;j <m[i] ; j++  )
            printf("%3d",block[i][j]);
            printf("\n");
    
        
    
    
}
```

