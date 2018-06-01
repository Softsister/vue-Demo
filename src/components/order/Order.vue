<template>
  <div class="box">
    <input type="file" id="files"  @change="filesss"  style="display: none;"/>
    <button @click="handleclick" :style="config">上传图片</button>
  </div>
</template>

<script>
// import http from '../api/file.js'
export default {
  props: ['config'],
  name: 'max',
  data () {
    return {
      todo: '上传图片',
      imglists: [],
      filelist: []
    }
  },
  methods: {
    pfuncs (d) {
      if (d === '评论成功') {
        this.comment_list()
      }
    },
    handlecell () {
      alert('1')
    },
    sub () {
      const data = {
        todouri: this.imglists,
        todofile: this.filelist
      }
      this.$emit('pfuncs', data)
    },
    radioselect (d) {
      this.activeid = d
    },
    filesss (e) {
      var files = e.target.files, typelist = ['image/jpeg', 'image/png'], filetype, isPic // 文件类型是否合法标识
      filetype = files[0].type
      isPic = typelist.some(function (item) { return item === filetype })
      if (isPic) {
        this.filelist[0] = files[0]
        this.imglist(files[0])
      } else {
        alert('不是图片')
      }
    },
    imglist (file) {
      var t = this
      var reader = new FileReader()
      // 读取文件作为URL可访问地址
      reader.readAsDataURL(file)
      reader.onload = function (e) {
        // this 对象为reader
        // reader.result 表示图片地址
        t.imglists = reader.result
        t.sub()
      }
    },
    handleclick () {
      document.getElementById('files').click()
    }
  },
  components: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .box{
    display: inline-block;
  }
</style>
