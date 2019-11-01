# 范式
## 函数依赖
```latex
X \to Y:Y函数依赖于X,X是决定属性组，X是决定因素    
平凡的函数依赖:X \to Y,Y \subset X     
X \to Y,Y \to X 记作X \gets \to Y     
若Y不函数依赖于X,则记作X \not\to Y
```
Y是X的子集  

  
 

## 第一范式
> [!NOTE]
> 作为一个二维表，关系要符合一个基本条件：每一个分量必须是不可分的数据项。满足了这个条件的关系模式就属于第一范式(1NF)

## 第二范式
> [!NOTE]
> 若R是1NF，且每一个非主属性完全函数依赖于任何一个候选码，则R是2NF

> [!NOTE]
> 有关系模式S-L-C(Sno,Sdept,Sloc,Cno,Grade),其中Sloc为学生住处，并且每一个系的学生住在同一个地方。S-L-C的码是(Sno,Cno),则函数依赖有  
(Sno,Cno) F-> Grade   
Sno->Sdept,(Sno,Cno) p-> Sdept    
Sno->Sloc ,(Sno,Cno) p->Sloc    
Sdept->Sloc     
可以看到非主属性Sdept和Sloc不完全函数依赖于码(Sno,Cno)    

> [!NOTE]
> 解决方法：将S-L-C(Sno,Sdept,Sloc,Cno,Grade),分解为SC(Sno,Cno,Grade)和S-L(Sno,Sdept,Sloc)使得非主属性对码都是完全函数依赖了。

## 第三范式
