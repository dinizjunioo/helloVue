<template>
  <div class="container">
    <hr/>
    <div class="form-todo form-group">
      <p>
        <input placeholder="nome" type="text" name="author" class="form-control" v-model="name" />
      </p>
      <p>
        <textarea placeholder="comentario"  name="message" class="form-control" v-model="message" ></textarea>
      </p>
      <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
    </div>

    <div class="list-group">
      <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
        <span class="comment__author"><strong>Autor: {{comment.name}}</strong></span>
        <p>Comentário: {{comment.message}}</p>
        <div>
          <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
        </div> 
      </div>
    </div> 
    <hr />
  </div>
</template>

<script>
export default {
  data() {
    return { 
      comments: [],
      name:'',
      message:''
    }
  },
  methods:{
    addComment(){
      if(this.message.trim() === ''){
        return;
      }
      this.comments.push({
        name: this.name,
        message: this.message
      });
      this.name='';
      this.message='';

    },
    removeComment(index){
      this.comments.splice(index,1);
    }
  },
  computed:{
    allComments(){
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === '' ? 'Anônimo' : comment.name
      }))
    }
  },
  watch:{
    comments (val){
      console.log('val',val)
    }
  }
}

</script>
