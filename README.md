# ds

(1) R commands

#create variable and assign data
> x<-10
> x
#create string 
> myname="eric"
> myname
#using vectors and factor
> layers<-c('pracels','streets','railroads','streams')
> length(layers)
> layers[3]
> layerIds<-c(1,2,3,4)
> combinedVector<-c(layers,layerIds)
> combinedVector
#mean median and mode
> s<-c(10,20,30,40,50)
> mean(s) > median(s)  > max(s) >min(s)
#factor
> land.type<-factor(c("residentials","commercial","commercial","agricultural"),levels = c("residentials","commercial"))
> table(land.type)
#list
> my.list<-list("streets",2000,TRUE,"parcels")
> my.list
#using data classes
> mx<-matrix(c(2,4,3,6,5,1),nrow=2,ncol=3,byrow=TRUE)
> mx
#adding column names
> colnames(mx)<-c("ii","io","pi")
> mx

#Data exploration and visualization using Tidyverse



(4)Practical of Principal Component Analysis
Declaring Variables 
➢Gpa <- c(3.2,3.9,2.9,3.0) 
➢Gre <- c(1270,1600,1500,1400) 
➢Professorrating <- c(38,42,22,32) 
➢Student <- data.frame(Gpa,Gre,Professorrating) 
>Student
➢data=cor(Student) 
>data
>eigen(data)
>barplot(eigen(data)$vectors)
>pc1=1stcol 1stno * Gpa+ 1stcol 2ndno * Gre+ 1stcol 3rdno*Professorrating 
same for pc2 and pc3
>➢data.frame(Gpa,Gre,Professorrating,pc1) 
same for pc2 and pc3

(5)clustering

data("USArrests")   # Loading the data set
df <- scale(USArrests) # Scaling the data
head(df,n=3)  # View the firt 3 rows of the data
#create a beautiful graph of the clusters generated with the kmeans() function, will use the factoextra package
install.packages("factoextra")  
library(factoextra)
#provides a convenient solution to estimate the optimal number of clusters
fviz_nbclust(df, kmeans, method = "wss")+geom_vline(xintercept = 4, linetype = 2)
#Computing k-means clustering
set.seed(123)   
km.res <- kmeans(df, 4, nstart = 25)
print(km.res)   ## Print the results
aggregate(USArrests, by=list(cluster=km.res$cluster), mean)
dd <- cbind(USArrests, cluster = km.res$cluster)
head(dd)
# Cluster number for each of the observations
km.res$cluster
head(km.res$cluster, 4)
km.res$size   ## Cluster size
km.res$centers
#Visualizing k-means clusters
fviz_cluster(km.res, df, geom = "point", ellipse.type = "norm")
## Use hcut() which compute hclust and cut the tree
hc.cut <- hcut(df, k = 3, hc_method = "complete") 
# Visualize dendrogram
fviz_dend(hc.cut, show_labels = FALSE, rect = TRUE)
# Visualize cluster
fviz_cluster(hc.cut, ellipse.type = "convex")

(6)time series forcasting

rainfall <- c(799,1174.8,865.1,1334.6,635.4,918.5,685.5,998.6,784.2,985,882.8,1071)
rainfall.timeseries <- ts(rainfall,start = c(2012,1),frequency = 12)
print(rainfall.timeseries)
png(file = "rainfall.png")
plot(rainfall.timeseries)
dev.off()
plot(rainfall.timeseries)

(7) simple/multiple regression

simple== >x<-c(125,...174) 10 input of heights
>y<-c(63,58...70)  10 input of weights
>relation<-lm(y~x)
>print(relation)
>print(summary(relation))
>a<-data.frame(x=170)
>result<-predict(relation,a)
print(result)

>plot(y,x,main="height weight regression",abline(lm(x~y)),xlab="weight in kg",ylab="height in cm")

Multiple regression
input<-mtcars[c("mpg","disp","hp","wt")]
print(head(input))
model<-lm(mpg~disp+hp+wt,data=input)
print(model)
a<-coef(model)[1]
print(a)
b<-coef(model)[2]
print(b)
c<-coef(model)[3]
print(c)
d<-coef(model)[4]
print(d)



(8) Logistics Regression





(9) hypothsis testing
#one sample test
x<-c(6.2,....11.9
t.test(x-9, alternative="two.sided",conf.level=0.95)
#two sample test
x=c(142,... ,523)
y=c(125,... ,521)
test2<-t.test(x,y,alternative="two.sided",mu=0,var.equal=F,conf.level=0.95)
test2
#prop.test(43,100,p=.5,correct=False)
#csv file
set directory-->session--->set working directory)
create csv file
>data<-read.table("data-tr.csv",header=True,sep=";")
>t.test(data,mu=72,alternative="greater")


(10)one way anova
pain=c(4,5,....4) [15 input]
drug=c(rep("A",5),rep("B",5),rep("C",5))
migraine=data.frame(pain,drug)
migraine
plot(pain~drug,data=migraine)
results=aov(pain~drug,data=migraine)
summary(results)
pairwise.t.test(pain,drug,p.adjust="bonferroni")

#TukeyHsd
>results=aov(pain~drug,data=migraine)
>TukeyHSD(results,conf.level=0.95)

(11)Decision Tree
install rattle packages from cran-rstudio
rattle 3.0.2
install package click and package archieve file and browser that file
>library("rattle"
>summary(weather)
>install.packages("rpart")
>library(rpart)
>weather2<-subset(weather,select=-c(RISK_MM))
>model<-rpart(formula=RainTomorrow ~., data=weather2, method="class")
>summary(model)
>library(rpart.plot)
>fancyRparPlot(model,main="Rain Tomorrow", sub="chapter 12")











