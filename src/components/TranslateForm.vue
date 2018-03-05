<template>
	<div  id="translateForm">
		<div class="container">
			<form id="transForm" class="well form-inline" @submit="formSubmit">
				<input class="form-control" type="text" v-model="textToTranslate" placeholder="你好" name="">
				<select class="form-control" v-model="language">
					<option value="en">English</option>
					<option value="ru">Russian</option>
					<option value="ko">Korean</option>
					<option value="ja">Janpenese</option>
				</select>
				<button class="btn btn-primary">翻译</button>
			</form>
		</div>
	</div>
</template>
<script type="text/javascript">
	export default{
	name:'tranlateForm',
	data:function(){
       return {textToTranslate:'',
               language:''
           }
    },
	methods:{
       formSubmit(e){
          this.$emit('formSubmit',this.textToTranslate,this.language)
          e.preventDefault();
        }
     },
     created:function(){
     this.language="en";
 }
}

</script>
<style type="text/css" >
#transForm{
	border:1px soild #ccc;
	border-radius:10px;
}
.container{
	margin:40px auto;

	width:500px;
}

</style>