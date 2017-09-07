# -
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>删除信息</title>
</head>
<link href="css/bootstrap.css" rel="stylesheet" type="text/css">
  <!---这里是调用的 jqurey 和 bottstrap vue.js代码 复制代码时请自己调用以下三个js-->
<!--<script src="jquery11.js"></script>
<script src="bootstrap.js"></script>
<script src="vuejs/vue.js"></script>-->
<body>
<div id="box">
	<div class="container">
    	<form fole="form">
        	<div class="form-group">
            	<label for="username">用户名:</label>
            	<input type="text" id="username" class="form-control" placeholder="请输入用户名" v-model="username">
            </div>
            <div class="form-group">
            	<label for="age">年龄:</label>
            	<input type="text" id="age" class="form-control" placeholder="请输入年龄" v-model="age">
            </div>
            <div class="form-group">
            	<input type="button" value="添加" class="btn btn-primary" v-on:click="add()">
                <input type="reset" value="重置" class="btn btn-danger">
            </div>
        </form>
        <hr>
        <table class="table table-bordered table-hover">
        	<caption class="h2 text-info text-center">用户信息表</caption>
            <tr class="text-danger">
            	<th class="text-center">序号</th>
                <th class="text-center">名字</th>
                <th class="text-center">年龄</th>
                <th class="text-center">操作</th>
            </tr>
            <tr class="text-center" v-for="value in myData">
                <td>{{$index+1}}</td>
                <td>{{value.name}}</td>
                <td>{{value.age}}</td>
                <td><button class="btn btn-primary btn-sm" data-toggle="modal" data-target="#layer" v-on:click="nowIndex=$index">删除</button></td>
            </tr>
            <tr v-show="myData.length!=0">
            	<td colspan="4" class="text-right"><button class="btn btn-danger btn-sm"  data-toggle="modal" data-target="#layer" v-on:click="nowIndex=-2">删除全部</button></td>
            </tr>
            <tr v-show="myData.length==0">
            	<td colspan="4" class="text-center text-muted"><p>暂无数据....</p></td>
            </tr>
        </table>
    </div>
    <!--弹出框--->
    <div role="dialog" class="modal fade" id="layer">
    	<div class="modal-dialog">
        	<div class="modal-content">
            	<div class="model-header">
                	<button class="close" data-dismiss="modal">
                    	<span>&times;</span>
                    </button>
                    <h4>确认删除么?</h4>
                </div>
                <div class="modal-body text-right">
                	<button class="btn btn-primary btn-sm" data-dismiss="modal">取消</button>
                    <button class="btn btn-danger btn-sm" data-dismiss="modal" v-on:click="deleMsg(nowIndex)">确认</button>
                </div>
            </div>
        </div>
    </div>
</div>
</body>
</html>
<!--下面是调用的vue.js代码-->
<script>
window.onload = function(){
	var c= new Vue({
		el:'#box',
		data:{
			myData:[],
			username:'',
			age:''
		},
		methods:{
			add:function(){
				this.myData.push({
					name:this.username,
					age:this.age,
					nowIndex:-100	
				});
				this.username='';
				this.age='';
			}	,
			deleMsg:function(n){
				if(n==-2){
					this.myData=[];
				}else{
					this.myData.splice(n,1);	
				}
				
			}
		}
	});
};
	
</script>

