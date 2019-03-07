<template>
  <div>
    <el-row type="flex" justify="end">
      <el-button @click="addClass" type="success">增加教室</el-button>
    </el-row>
    <el-row>
      <el-table
          :data="klassArray"
          style="width: 100%">
        <el-table-column
            prop="name"
            label="班级名">
        </el-table-column>
        <el-table-column
            prop="students.length"
            label="人数">
        </el-table-column>
        <el-table-column align="center" label="操作">
          <template slot-scope="scope">
            <el-button type="primary" size="small" @click="addStudent(scope.row)">增加学生</el-button>
            <el-button type="danger" size="small" @click="deleteClass(scope.row)">删除班级</el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-row>
    <el-dialog title="增加班级" :visible.sync="addClassVisible" width="30%">
      <el-input placeholder="请输入班级名" v-model="classInfo.name">
        <template slot="prepend">班级名</template>
      </el-input>
      <span slot="footer" class="dialog-footer">
    <el-button @click="addClassVisible = false">取 消</el-button>
    <el-button type="primary" @click="confirmAddClass">确 定</el-button>
  </span>
    </el-dialog>
  </div>
</template>

<script>
  import lodash from 'lodash'
  let klassArray = [
    {id: 1, name: "班级一", students: []},
    {id: 2, name: "班级二", students: []},
    {id: 3, name: "班级三", students: []},
  ];
  export default {
    name: "ClassInfo",
    data() {
      return {
        addClassVisible:false,
        klassArray: klassArray,
        classInfo: {
          name: ""
        }
      }
    },
    methods: {
      addStudent(row){
      },
      addClass(){
        this.addClassVisible = true;
      },
      confirmAddClass(){
        let id = lodash.max(lodash.map(klassArray,'id').sort())+1;
        klassArray.push({id, name: this.classInfo.name, students:[]});
        this.addClassVisible = false;
      },
      deleteClass(row){
        this.$confirm(`是否确定删除班级:${row.name}?`, '提示', {type: 'warning'}).then(()=>{
          klassArray.splice(klassArray.indexOf(row), 1);
        })
      },
    }
  }
</script>

<style scoped>

</style>