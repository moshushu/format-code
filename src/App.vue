<template>
  <div>
    <div>
      <vue-editor />
      <!-- primary 主要按钮 -->
      <div>
        <el-button type="primary" @click="addDomain">新增一行</el-button>
      </div>
      <br>
      <div>
        <el-form :model="formatDataForm" ref="formatDataForm" label-width="100px" :inline="true">

          <div v-for="(domain, index) in formatDataForm.domains" :key="index">

            <el-form-item :key="domain.key" label="实体中文名">
              <el-input v-model="domain.entityNameCn" size="small" />
            </el-form-item>

            <el-form-item :key="domain.key" label="实体英文名">
              <el-input v-model="domain.entityNameEn" size="small" />
            </el-form-item>

            <el-form-item :key="domain.key" label="字段名称">
              <el-input v-model="domain.fieldName" size="small" />
            </el-form-item>

            <el-form-item :key="domain.key" label="字段类型">
              <el-select v-model="domain.fieldType" size="small">
                <el-option label="字符串" value="CharField"></el-option>
                <el-option label="布尔" value="BooleanField"></el-option>
                <el-option label="整数" value="IntegerField"></el-option>
                <el-option label="单选" value="SelectionField"></el-option>
                <el-option label="文本" value="TextField"></el-option>
                <el-option label="日期" value="DateField"></el-option>
                <el-option label="浮点数" value="FloatField"></el-option>
                <el-option label="多选" value="MultiSelectionField"></el-option>
              </el-select>
            </el-form-item>

            <el-form-item :key="domain.key" label="S和D">
              <el-switch v-model="domain.isEnable" inline-prompt active-text="是" inactive-text="否" />
            </el-form-item>

            <el-form-item :key="domain.key" label="必填">
              <el-switch v-model="domain.required" inline-prompt active-text="是" inactive-text="否" />
            </el-form-item>

            <el-form-item :key="domain.key" label="唯一">
              <el-switch v-model="domain.unique" inline-prompt active-text="是" inactive-text="否" />
            </el-form-item>

            <el-form-item :key="domain.key" label="索引">
              <el-switch v-model="domain.index" inline-prompt active-text="是" inactive-text="否" />
            </el-form-item>

          </div>

        </el-form>
      </div>
    </div>
  </div>
</template>

<script>
import VueEditor from './components/vueEditor.vue'
export default {
  name: 'dynamicForm',
  // 引用vue-prism-editor 组件
  components: {
    'vue-editor': VueEditor
  },
  data() {
    return {
      formatDataForm: {
        domains: [{
          entityNameCn: '', // 实体中文名称
          entityNameEn: '', // 实体英文名称
          fieldName: '',    //字段名称
          fieldType: '',    //字段类型
          isEnable: true, //是否填写String和Description"
          required: false, // 是否必填
          unique: false, // 是否唯一
          index: false, // 可否索引
          // 单选多选默认携带选项框架
          key: Date.now()
        }],
      },
    }
  },
  methods: {
    addDomain() {
      this.formatDataForm.domains.push({
        entityNameCn: '', // 实体中文名称
        entityNameEn: '', // 实体英文名称
        fieldName: '',    //字段名称
        fieldType: '',    //字段类型
        isEnable: true, //是否填写String和Description"
        required: false, // 是否必填
        unique: false, // 是否唯一
        index: false, // 可否索引
        // 单选多选默认携带选项框架
        key: Date.now()
      });
    },
  },
}
</script>

<style>

</style>
