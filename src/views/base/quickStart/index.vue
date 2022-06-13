<!-- 
    @description quickStart
    @author zhangcj
    @date 2022-06-13 16:45:56 
 -->
<template>
  <div class="quick-start-container">
    <canvas ref="glDom" class="gl-dom"></canvas>
  </div>
</template>
<script>
import vertexShader from "../../shader/base/quickStart/vertexShader.glsl"
import fragmentShader from "../../shader/base/quickStart/fragmentShader.glsl"
export default {
  name: "",
  mounted() {
    this.glInit()
  },
  components: {},
  methods: {
    glInit() {
      console.log(vertexShader)
      console.log(fragmentShader)
      const canvas = this.$refs.glDom
      const gl = canvas.getContext("webgl")
      const program = gl.createProgram()
      //把顶点着色对象装进程序对象中
      gl.attachShader(
        program,
        this.loadShader(gl, gl.VERTEX_SHADER, vertexShader)
      )
      //把片元着色对象装进程序对象中
      gl.attachShader(
        program,
        this.loadShader(gl, gl.FRAGMENT_SHADER, fragmentShader)
      )
      //连接webgl上下文对象和程序对象
      gl.linkProgram(program)
      //启动程序对象
      gl.useProgram(program)
      //将程序对象挂到上下文对象上
      gl.program = program

      // 指定将要用来清理绘图区的颜色
      gl.clearColor(0, 0.0, 0.0, 1.0)
      // 清理绘图区
      gl.clear(gl.COLOR_BUFFER_BIT)
      // 绘制顶点
      gl.drawArrays(gl.POINTS, 0, 1)
    },
    loadShader(gl, type, source) {
      //根据着色类型，建立着色器对象
      const shader = gl.createShader(type)
      //将着色器源文件传入着色器对象中
      gl.shaderSource(shader, source)
      //编译着色器对象
      gl.compileShader(shader)
      //返回着色器对象
      return shader
    },
  },
}
</script>
<style lang="scss" scoped>
.quick-start-container {
  height: 100vh;
  width: 100%;
  .gl-dom {
    height: 100vh;
    width: 100%;
  }
}
</style>
