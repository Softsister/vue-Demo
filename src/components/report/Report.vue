<template>
    <div>
      <el-upload
        class="upload-demo"
        action="https://jsonplaceholder.typicode.com/posts/"
        :on-preview="handlePreview"
        :on-remove="handleRemove"
        :before-remove="beforeRemove"
        :before-upload="beforeAvatarUpload"
        multiple
        :file-list="fileList"
        accept=".mp4,.avi">
        <img v-if="imageUrl" :src="imageUrl" class="avatar">
        <el-button size="small" type="primary">点击上传</el-button>
      </el-upload>
    </div>
</template>

<script>
export default {
  data () {
    return {
      imageUrl: '',
      fileList: []
    }
  },
  methods: {
    handleRemove (file, fileList) {
      console.log(file, fileList)
    },
    handlePreview (file) {
      console.log(file)
    },
    beforeRemove (file, fileList) {
      return this.$confirm(`确定移除 ${file.name}？`)
    },
    beforeAvatarUpload (file) {
      // const isJPG = file.type === 'image/jpeg'
      // const isLt2M = file.size / 1024 / 1024 < 2
      //
      // if (!isJPG) {
      //   this.$message.error('上传头像图片只能是 JPG 格式!')
      // }
      // return isJPG && isLt2M
      return file
    }
  }
}
</script>

<style scoped>

</style>
