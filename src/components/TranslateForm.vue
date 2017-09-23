<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form id="transForm" class="well form-inline" v-on:submit="formSubmit">
         <input class="form-control" type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容">
         <select class="form-control" v-model="language">
           <option value="en">English</option>
           <option value="zh">Chinese</option>
           <option value="ru">Russian</option>
           <option value="ko">Korean</option>
           <option value="fr">French</option>
         </select>
         <input class="btn btn-primary" type="submit" value="翻译">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data:function(){
    return{
      textToTranslate:"",
      language:""
    }
  },
  methods:{
    formSubmit:function(e){
      // alert(this.textToTranslate);
      //把子组件的数据传给父组件，此处formSubmit与上文formSubmit无任何关联,可重新命名
      this.$emit("formSubmit",this.textToTranslate,this.language); 

      e.preventDefault();
    }
  },
  created:function(){
    this.language = "en";
  }
}
</script>

<style>
#transForm{
  border: 1px soild #ccc;
  border-radius: 10px;
}

#translateForm .well{
  background-color: white;
}

</style>
