# 范式
## 函数依赖
```latex
X \to Y:Y函数依赖于X,X是决定属性组，X是决定因素    \\
非平凡的函数依赖:X \to Y,但Y \not\to X则称X \to Y是非平凡的函数依赖 \\
平凡的函数依赖:X \to Y,Y \subset X       \\
X \to Y,Y \to X 记作X \gets \to Y     \\
若Y不函数依赖于X,则记作X \not\to Y    \\
Y对X的完全函数依赖,记作X \xrightarrow{F} Y:在R(U)中,如果X \to Y,并且对于X的任何一个真子集X',都有X' \not\to Y \\
Y对X的部分函数依赖,记作X \xrightarrow{P} Y:若X\to Y但Y不完全函数依赖于X
定义6.3 在R(U)中,如果X\to Y (Y \not\subset X),Y \not \to X,Y \to Z,Z \not \subset Y \\
则称Z对X传递函数依赖.记作X \xrightarrow{传递} Z \\
定义6.4设K为R<U,F>中的属性或属性组合,若K \xrightarrow{F},则K为R的候选码（candidate key）。\\
如果U是完全函数依赖于K,而不是部分函数依赖于K。如果U部分函数依赖于K，即为K\xrightarrow{P}U,则K称为超码(SuperKey)。\\
候选码是最小的超码，K的任意一个真子集都不是候选码。\\
若候选码多于一个，则选定其中一个为主码(primary key)。\\
定义6.5关系模式R中属性或属性组X并非R的码,但X是另一个关系模式的码。则称X是R的外部码（foreign key），也称外码。\\
如在SC(\underline{Sno},\underline{Cno},Grade)中,Sno不是码,\\
但Sno是关系模式S(\underline{Sno},Sdept,Sage)的码,则Sno是关系模式SC的外码。\\
主码与外码提供了一个表示关系间联系的手段 \\
定义6.6若R\in 1NF,且每一个非主属性完全函数依赖于任何一个候选码,则R \in 2NF。
定义6.7设关系模式R<U,F>\in 1NF,若R中不存在这样的码X,属性组Y及非主属性Z(Y \not \subset Z)\\
使得X \to Y,Y \to Z 成立,Y \not \to X,则称R<U,F> \in 3NF \\


```

  
 

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
