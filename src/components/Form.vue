<template>
  <el-card class="form-card">
    <el-form :model="formData" ref="addItemForm" :rules="rules" label-position="top">
      <el-form-item label="Тип " prop="type">
        <el-select class="type-select" v-model="formData.type" placeholder="Выбирите тип">
          <el-option label="Доходы" value="INCOME" />
          <el-option label="Расходы" value="OUTCOME" />
        </el-select>
      </el-form-item>

      <el-form-item label="Коментарий" prop="comment">
        <el-input v-model="formData.comment" placeholder="Введите комментарий" />
      </el-form-item>

      <el-form-item label="Значение" prop="value">
        <el-input v-model.number="formData.value" />
      </el-form-item>

      <el-button class="form-btn" @click="onSubmit" type="primary">Добавить</el-button>
    </el-form>
  </el-card>
</template>


<script>
export default {
  name: 'Form',
  data: () => ({
    formData: {
      type: 'INCOME',
      comment: '',
      value: 0
    },
    rules: {
      type: [
        { required: true, message: 'Пожалуйста выбирите тип', trigger: 'blur' }
      ],
      comment: [
        {
          required: true,
          message: 'Введите коментарий',
          trigger: 'blur'
        }
      ],
      value: [
        {
          required: true,
          message: 'Введите значение',
          trigger: 'blur'
        },
        {
          type: 'number',
          message: 'Значение должно быть числом',
          trigger: 'change'
        }
      ]
    }
  }),
  methods: {
    onSubmit() {
      this.$refs.addItemForm.validate(valid => {})
    }
  }
}
</script>

<style scoped>
.form-card {
  max-width: 768px;
  margin: 0 auto 80px;
  text-align: left;
}
.type-select {
  width: 100%;
}
.form-btn {
  margin: 0 auto;
  display: block;
}
</style>