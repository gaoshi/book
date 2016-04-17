### 基于Git的团队开发

#### 一、版本管理时的一些问题:
	1.如何开始一个Feature的开发，而不影响其他Feature?
	2.由于使用Git很容易创建新的分支，当分支多了，如何去管理分支，时间久了，如何知道每个分支是干什么的?
	3.哪些分支已经合并回主干了？
	4.如何进行Release的管理？开始一个Release的时候如何冻结Feature，如何在Prepare Release的时候，可以继续开发新的功能？
	5.线上出现Bug，如何快速修复？而且修复的代码要包含到开发人员的分支以及下一个Release?
	
#### 二、Git各开发分支说明：

	1.Master分支:这个分支最近发布到生产环境的代码，最近发布的Release，这个分支只能从其他分支合并，不能在这个分支直接修改

	2.Develop分支:这个分支是我们是我们的主开发分支，包含所有要发布到下一个Release的代码，这个主要合并与其他分支，比如Feature分支

	3.Feature分支:这个分支主要是用来开发一个新的功能，一旦开发完成，我们合并回Develop分支进入下一个Release。如:some-feature命名的分支

	4.Release分支:当需要发布一个新的Release时候，我们基于Develop分支创建一个Release分支，完成Release后，我们合并到Master和Develop分支

	5.Hotfix分支：Hotfix分支是基于Master分支创建，当我们在Master发现新的Bug时候，我们需要创建一个Hotfix, 完成Hotfix后，我们合并回Master和
	Develop分支，所以Hotfix的改动会进入下一个Release
	
#### 三、基于Git分支开发的流程图(Git Flow)：
<img src="http://s17.mogucdn.com/p1/160224/upload_ie4tay3ggzsgmolfgyzdambqgqyde_1150x1524.png" 
height=800 width=610 align="middle">>

#### 四、Git Flow如何工作

 ***`1.Develop和Master分支:`***
 	
	Master分支：是线上代码的备份分支，所有在Master分支上的Commit应该Tag，每当发布一个线上版本的时候需要打Tag
![alt text](http://s16.mogucdn.com/p1/160224upload_ie3tooldgfsdiylfgyzdambqgayde_614x148.png "Develop和Master分支")

<br>
-------------
 ***`2.Feature分支:`***
  
	Feature分支:功能开发分支，Feature分支开发完后，必须合并回Develop分支, 合并完后一般会删除这个Feature分支，也可以保留
  	
![alt text](http://s17.mogucdn.com/p1/160224upload_ifqwcnjrmyzdkylfgyzdambqgyyde_614x268.png "Feature分支")
  
<br>
-------------
 ***`3.Release分支:`***
 
	Release分支基于Develop分支创建，拉完Release分支之后，我们可以在这个Release分支上测试，修改Bug等。(注意：一旦打了Release分支之后不要从
	Develop分支上合并新的改动到Release分支)。发布Release分支时，合并Release到Master和Develop，同时在Master分支上打个Tag记住Release版本
	号，然后可以删除Release分支
  
![alt text](http://s16.mogucdn.com/p1/16022upload_ifrdmzlfmm2tkylfgyzdambqmeyde_614x320.png "Release分支")
 
<br>
----------
 ***`4.Hotfix分支:`***
 
	Hotfix分支基于Master分支创建，主要是线上出现Bug需要修复时，修复后合并回Master和Develop分支，同时在Master上打一个Tag
	
![alt text](http://s17.mogucdn.com/p1/160224/upload_ie3tkzrymnqtkylfgyzdambqgayde_614x380.png "Hotfix分支")


#### 五、其他

***`一些参考资料`***

1.[A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
	


	
	
