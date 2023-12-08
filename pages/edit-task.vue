<template lang="pug">
el-container
    el-row
    el-col(:span="12")
        el-card
        h1 Modifier la tâche
        el-form(:model="editedTask" label-position="top" ref="editedTaskForm" :rules="taskFormRules" size="mini")
            el-form-item(label="Titre" prop="title")
            el-input(v-model="editedTask.title" placeholder="Entrez le titre de la tâche")
            el-form-item(label="Description" prop="description")
            el-input(v-model="editedTask.description" type="textarea" placeholder="Entrez la description de la tâche")
            el-form-item
            el-button(type="primary" @click="saveChanges") Enregistrer
</template>

<script>
export default {
data() {
    return {
    editedTask: {
        id: null,
        title: '',
        description: ''
    },
    taskFormRules: {
        title: [{ required: true, message: 'Veuillez entrer le titre de la tâche', trigger: 'blur' }],
        description: [{ required: true, message: 'Veuillez entrer la description de la tâche', trigger: 'blur' }]
    }
    };
},
created() {
    const taskId = this.$route.params.id;
    
    this.editedTask.id = taskId;
    this.editedTask.title = 'Titre de la tâche';
    this.editedTask.description = 'Description de la tâche';
},
methods: {
    saveChanges() {
    this.$refs.editedTaskForm.validate((valid) => {
        if (valid) {
        console.log('Modifications enregistrées :', this.editedTask);
        this.$router.push('/task-list');
        } else {
        return false;
        }
    });
    }
}
};
</script>
