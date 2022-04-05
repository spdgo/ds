(1) R commands

#create variable and assign data
* x<-10
* x
#create string 
* myname="eric"
* myname
#using vectors and factor
* layers<-c('pracels','streets','railroads','streams')
* length(layers)
* layers[3]
* layerIds<-c(1,2,3,4)
* combinedVector<-c(layers,layerIds)
* combinedVector
#mean median and mode
* s<-c(10,20,30,40,50)
* mean(s) * median(s)  * max(s) *min(s)
#factor
* land.type<-factor(c("residentials","commercial","commercial","agricultural"),levels = c("residentials","commercial"))
* table(land.type)
#list
* my.list<-list("streets",2000,TRUE,"parcels")
* my.list
#using data classes
* mx<-matrix(c(2,4,3,6,5,1),nrow=2,ncol=3,byrow=TRUE)
* mx
#adding column names
* colnames(mx)<-c("ii","io","pi")
* mx

#Data exploration and visualization using Tidyverse


(2)NOSQL AND COUCHDB  nosql and couchdb Practical of Data collection, Data curation and management 

>library('sofa') 

>x<-Cushion$new() 

>x$ping() 

>db_create(x,dbname='devyani' )

>version

>db_list(x) 

>doc1<-'{"Rollno":"01","Name":"devyani","Grade":"O"}' 

>doc_create(x,doc1,dbname='devyani',docid = "a_1") 

>doc2<-'{"Rollno":"02","Name":"Abc","Grade":"O"}'

>doc_create(x,doc2,dbname='devyani',docid = "a_2") 

>doc3<-'{"Rollno":"03","Name":"Def","Grade":"O","Remark":"Pass"}' >doc_create(x,doc3,dbname='devyani',docid = "a_3") 
>db_changes(x,"devyani" ) 

>db_query(x,dbname="devyani",selector=list('_id'=list('$gt'=NULL)))$doc

>db_query(x,dbname="devyani",selector=list(Grade="O"))$doc 

db_query(x,dbname="devyani",selector=list(Remark="Pass"))$docs 

db_query(x,dbname="devyani",selector=list('Rollno'=list('$gt'='02')),fields = c("Name","Grade"))$docs

>library(jsonlite) 

>res<-db_query(x,dbname="devyani",selector=list('_id'=list('$gt'=NULL)),fields = c("Rollno","Name","Grade","Remark"),as="json") 

>fromJSON(res)$docs 

doc_delete(x,dbname = "devyani",docid = "a_2")

doc_get(x,dbname = "devyani",docid = "a_2") 

>doc2<-'{"Name":"Abc","Bear":"Test","Note","Yummy","Note2","Yay"}' 

>doc_update(x,dbname = "devyani",doc=doc2,doc_id="a_3",rev="1- dcd9ae2cc689513f463046f26ca2ce8d")



(3)Practical of Data collection, Data curation and management for 
Large-scale Data system (such as MongoDB) What is Data Curation?
Commands: 

> use beginnersbookdb

> db.createCollection("got3")

>var abc=[ { "_id":ObjectId("59db2e73ce524b733f14dd65"), "name":"Jon Snow", "age":32  
Insert

> db.got3.insert(abc); 

> db.got3.find().pretty() 
Update 

> db.got3.update({"name":"Jon Snow"},{$set:{"name":"Kit Harington"}}) 

> db.got3.update({"name":"Jon Snow"},{$set:{"name":"Kit Harington"}}) 

> db.got3.update({"name":"Jon Snow"},{$set:{"name":"Kit Harington","age":{$gt:30}}}) 

> db.got3.find().pretty() 
Update 

> db.got3.update({"age":{$gt:30}},{$set:{"name":"Kit Harington"}}) 

> db.got3.find().pretty() 

> db.got3.update({"age":{$gt:30}},{$set:{"age":40}})

> db.got3.find().pretty() 

Multiple Update 
> db.got3.update({"age":{$gt:30}},{$set:{"age":40},multi:true}) 

> db.got3.update({"age":{$gt:30}},{$set:{"age":40}},{multi:true}) 

> db.got3.find().pretty() 

> db.got3.update({"age":{$gt:10}},{$set:{"name":"Devyani"}}) 

> db.got3.find().pretty() 
Find by name 

> db.collection.find({"name":"Devyani"}).pretty() 

> db.got3.find({"name":"Devyani"}).pretty()

Update through save command

> db.got3.save({"id":ObjectId("59db2e73ce524b733f14dd65"),"name":"Jon Snow","age":30}) 

> db.got3.find().pretty() 

> db.students.find().pretty() 

Delete 

> db.got3.remove({"age":20}) 

> db.students.find().pretty() 

> db.got3.find().pretty() 

> db.got3.remove({"age":40},1) 

> db.got3.find().pretty() 

Remove all 

> db.got.remove({}) 

> db.got.find().pretty() 

Find by given id or name by 0 and 1 

> db.got3.find({"_id":0,"name":0,"age":0}) 

> db.got3.find({},{"_id":0,"name":0,"age":0}) 

> db.got3.find({},{"_id":1,"name":1,"age":1}) 

> db.got3.find({},{"_id":0,"name":1,"age":1}) 

> db.got3.find({},{"_id":0,"name":0,"age":0}) 

> db.got3.find({},{"_id":0,"name":0,"age":0,"id":0}) 

Projections

> use 

> db.student.find().pretty() 

> db.student.find({},{"_id":0,"name":1}) 

> db.student.find({},{"_id":0,"name":0,"class":1})

With 1  

> db.student.find({},{"_id":0,"class":1}) 

> db.student.find({},{"_id":0,"rollno":0,"name":0}) 

> db.student.find({},{"_id":0,"rollno":1,"name":1}) 

> db.student.find({rollno: {$gt:3}}).limit().pretty() 

> db.student.find({rollno: {$gt:3}}).limit(1).pretty() 

> db.student.find({rollno: {$gt:3}}).limit(1).skip(1).pretty() 

> db.student.find({},{"_id":0,"rollno":1}).sort({"rollno":1}) 

> db.student.find({},{"_id":0,"rollno":1,"name":1}).sort({"rollno":1}) 

Descending Order 

> db.student.find({},{"_id":0,"rollno":1}).sort({"rollno":-1}) 

> db.student.find({},{"_id":0,"rollno":1,"name":1}).sort({"name":-1}) 

Creating Index 

> db.student.createIndex({"name":1}) 

Get All Indexes 

> db.student.getIndexes() 

Drop an index 

> db.student.dropIndex({"name":1}) 


Drop all Indexes 


> db.student.dropIndexes()

(4)Practical of Principal Component Analysis
Declaring Variables 
➢Gpa <- c(3.2,3.9,2.9,3.0) 
➢Gre <- c(1270,1600,1500,1400) 
➢Professorrating <- c(38,42,22,32) 
➢Student <- data.frame(Gpa,Gre,Professorrating) 
*Student
➢data=cor(Student) 
*data
*eigen(data)
*barplot(eigen(data)$vectors)
*pc1=1stcol 1stno * Gpa+ 1stcol 2ndno * Gre+ 1stcol 3rdno*Professorrating 
same for pc2 and pc3
*➢data.frame(Gpa,Gre,Professorrating,pc1) 
*same for pc2 and pc3

(5)clustering

*data("USArrests")  
*df <- scale(USArrests) # Scaling the data
*head(df,n=3)  # View the firt 3 rows of the data
#create a beautiful graph of the clusters generated with the kmeans() function, will use the factoextra package
*install.packages("factoextra")  
*library(factoextra)
#provides a convenient solution to estimate the optimal number of clusters
*fviz_nbclust(df, kmeans, method = "wss")+geom_vline(xintercept = 4, linetype = 2)
#Computing k-means clustering
*set.seed(123)   
*km.res <- kmeans(df, 4, nstart = 25)
*print(km.res)   ## Print the results
*aggregate(USArrests, by=list(cluster=km.res$cluster), mean)
*dd <- cbind(USArrests, cluster = km.res$cluster)
*head(dd)
*km.res$cluster  #Cluster number for each of the observations
head(km.res$cluster, 4)
*km.res$size   ## Cluster size
*km.res$centers
#Visualizing k-means clusters
*fviz_cluster(km.res, df, geom = "point", ellipse.type = "norm")
*hc.cut <- hcut(df, k = 3, hc_method = "complete")    #Use hcut() which compute hclust and cut the tree
*fviz_dend(hc.cut, show_labels = FALSE, rect = TRUE)   #visualize dendogram
*fviz_cluster(hc.cut, ellipse.type = "convex")    # Visualize cluster

(6)time series forcasting

*rainfall <- c(799,1174.8,865.1,1334.6,635.4,918.5,685.5,998.6,784.2,985,882.8,1071)
*rainfall.timeseries <- ts(rainfall,start = c(2012,1),frequency = 12)
*print(rainfall.timeseries)
*png(file = "rainfall.png")
*plot(rainfall.timeseries)
*dev.off()
*plot(rainfall.timeseries)

(7) simple/multiple regression

simpler regression== 
*x<-c(125,...174) {@10 input of heights}
*y<-c(63,58...70)  10 input of weights
*relation<-lm(y~x)
*print(relation)
*print(summary(relation))
*a<-data.frame(x=170)
*result<-predict(relation,a)
*print(result)

*plot(y,x,main="height weight regression",abline(lm(x~y)),xlab="weight in kg",ylab="height in cm")

Multiple regression
*input<-mtcars[c("mpg","disp","hp","wt")]
*print(head(input))
*model<-lm(mpg~disp+hp+wt,data=input)
*print(model)
*a<-coef(model)[1]
*print(a)
*b<-coef(model)[2]
*print(b)
*c<-coef(model)[3]
*print(c)
*d<-coef(model)[4]
*print(d)



(8)Practical of Logistics Regression
*library(datasets)
* ir_data<- iris 
*head(ir_data)
* str(ir_data)
* levels(ir_data$Species)
* sum(is.na(ir_data))
* ir_data<-ir_data[1:100,]
* set.seed(100)
* samp<-sample(1:100,80) 
*ir_test<-ir_data[samp,]
* ir_ctrl<-ir_data[-samp,] 
*install.packages("ggplot2")
* library(ggplot2)
* install.packages("GGally")
* library(GGally) 
*ggpairs(ir_test)
* y<-ir_test$Species;
* x<-ir_test$Sepal.Length
* glfit<-glm(y~x, family = 'binomial') summary(glfit)
* newdata<- data.frame(x=ir_ctrl$Sepal.Length) 
*predicted_val<-predict(glfit, newdata, type="response") 
*prediction<-data.frame(ir_ctrl$Sepal.Length, ir_ctrl$Species,predicted_val)
* prediction
* qplot(prediction[,1], round(prediction[,3]), col=prediction[,2], xlab = 'Sepal Length', ylab = 'Prediction using Logistic Reg.')





(9) hypothsis testing
#one sample test
*x<-c(6.2,....11.9)
*t.test(x-9, alternative="two.sided",conf.level=0.95)
#two sample test
*x=c(142,... ,523)
*y=c(125,... ,521)
*test2<-t.test(x,y,alternative="two.sided",mu=0,var.equal=F,conf.level=0.95)
*test2
*prop.test(43,100,p=.5,correct=False)
#csv file
set directory--*session---*set working directory)
create csv file
*data<-read.table("data-tr.csv",header=True,sep=";")
*t.test(data,mu=72,alternative="greater")


(10)one way anova
*pain=c(4,5,....4) [15 input]
*drug=c(rep("A",5),rep("B",5),rep("C",5))
*migraine=data.frame(pain,drug)
*migraine
*plot(pain~drug,data=migraine)
*results=aov(pain~drug,data=migraine)
*summary(results)
*pairwise.t.test(pain,drug,p.adjust="bonferroni")

#TukeyHsd
*results=aov(pain~drug,data=migraine)
*TukeyHSD(results,conf.level=0.95)

(11)Decision Tree
install rattle packages from cran-rstudio
rattle 3.0.2
install package click and package archieve file and browser that file
*library("rattle"
*summary(weather)
*install.packages("rpart")
*library(rpart)
*weather2<-subset(weather,select=-c(RISK_MM))
*model<-rpart(formula=RainTomorrow ~., data=weather2, method="class")
*summary(model)
*library(rpart.plot)
*fancyRparPlot(model,main="Rain Tomorrow", sub="chapter 12")











