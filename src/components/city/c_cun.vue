<template>
	<div class="public cun ">
		<div class="main">
			<div class="main_content">
				<div class="filter">
					<div class="isFilter" @click="handleFilter"><img :class="isFilter ? 'rotate' : ''" src="../../../static/img/provincial/select_icon.png" /><span>{{isFilter ? '收起筛选' : '展开筛选'}}</span></div>
					<el-collapse-transition>
						<div class="filterBox" v-show="isFilter" style="padding: 36px 50px 46px 50px;">
							<el-form :inline="true" :model="filter" class="demo-form-inline">
								<el-form-item label="归属区县">
									<el-select v-model="filter.region" clearable placeholder="活动区域">
										<el-option label="区域一" value="shanghai"></el-option>
										<el-option label="区域二" value="beijing"></el-option>
									</el-select>
								</el-form-item>
								<el-form-item label="归属乡镇">
									<el-select v-model="filter.region" clearable placeholder="活动区域">
										<el-option label="区域一" value="shanghai"></el-option>
										<el-option label="区域二" value="beijing"></el-option>
									</el-select>
								</el-form-item>
								<el-form-item label="村名">
									<el-input v-model="filter.user" clearable placeholder="审批人"></el-input>
								</el-form-item>
								<el-form-item>
									<div style="width: 82px;
											height: 40px;
											background-color: #4a87c1;
											border-radius: 4px;line-height: 40px;
											text-align: center;">
										<div class="btn" style="padding:0px">查询</div>
									</div>
								</el-form-item>
							</el-form>
							<!-- <div class="filter_btn">
								<div class="btn btn1">查询</div>
							</div> -->
						</div>
					</el-collapse-transition>
				</div>
				<div class="table">
					<el-table ref="table" :data="tableData" tooltip-effect="dark" style="width: 99%;" height="100%" header-cell-class-name="tableTou" cell-class-name="tableRow" @selection-change="handleSelectionChange">
						<el-table-column type="index" label="序号" align="center" width="100px">
						</el-table-column>
						<el-table-column prop="villagers" label="村名" align="center" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="city" align="center" label="归属市州" width="110" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="county" align="center" label="归属区县" width="110" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="town" align="center" label="归属乡镇" width="110" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="name" align="center" label="村长姓名" width="110" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="phone" align="center" label="村长联系电话" width="140" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="yuwangname" align="center" label="村支书姓名" width="130" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="yuwangphone" align="center" label="村支书联系电话" width="150" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="secretaryname" align="center" label="驻村第一书记姓名" width="180" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="secretaryphone" align="center" label="驻村第一书记联系电话" width="200" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="Update" align="center" label="更新日期" width="110" show-overflow-tooltip>
						</el-table-column>
					</el-table>

				</div>
				<div class="fenye">
					<div class="fenye_title">共 {{total}} 条数据 每页 {{pageSize}} 条数据 共 {{Math.floor(total/pageSize) + (total%pageSize != 0 ? 1 : 0)}} 页</div>
					<el-pagination :current-page.sync="currentPage" :page-size="pageSize" layout="prev, pager, next, jumper" :total="total">
					</el-pagination>
				</div>
			</div>
		</div>
		<div class="footer">
			<my-footer></my-footer>
		</div>
	</div>
</template>

<script>
import footer from '@/components/com/footer'
export default {
	data() {
		return {
			isFilter: false, // 是否展开筛选
			filter: {

			},
			pageSize: 10,
			total: 21,
			currentPage: 1,

			tableData: [
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄按时打算大叔大叔大叔大叔大叔大叔大叔打时代发生的发生地方时代发生的发生的发的'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
				{
					date: '2016-05-03',
					name: '王小虎',
					address: '上海市普陀区金沙江路 1518 弄'
				},
			],
			multipleSelection: [],
		}
	},
	components: { 'my-footer': footer },
	methods: {
		handleFilter() {
			this.isFilter = !this.isFilter;
		},
		toggleSelection(rows) {
			if (rows) {
				rows.forEach(row => {
					this.$refs.multipleTable.toggleRowSelection(row);
				});
			} else {
				this.$refs.multipleTable.clearSelection();
			}
		},
		handleSelectionChange(val) {
			this.multipleSelection = val;
		}
	}
}

</script>

<style scoped>
.public {
  height: 100%;
  position: relative;
}
.footer {
  height: 60px;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
}
.main {
  position: absolute;
  top: 0;
  bottom: 60px;
  left: 0;
  right: 0;
  background: #eff2f7;
  padding: 20px 40px 0px 20px;
}
.main_content {
  height: 100%;
  background: rgba(255, 255, 255, 1);
  display: flex;
  flex-direction: column;
  border-radius: 3px;
  box-shadow: 0px 0px 120px 0px rgba(31, 32, 41, 0.05);
  overflow: auto;
}
.filter {
  height: 74px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.isFilter {
  width: 190px;
  height: 50px;
  background: rgba(244, 244, 244, 1);
  border-radius: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  font-size: 18px;
  font-weight: 400;
  color: rgba(61, 97, 150, 1);
}
.rotate {
  transform: rotate(180deg);
}
.isFilter > img {
  margin-right: 10px;
  transition: all 0.3s;
}
.filterBox {
  position: absolute;
  border-top: 1px solid rgba(238, 238, 238, 1);
  padding: 36px 50px 46px 50px;
  height: auto;
  z-index: 999;
  background-color: #fff;
  top: 74px;
  left: 0;
  right: 0;
  opacity: 0.99;
  box-shadow: 0px 10px 40px rgba(0, 0, 0, 0.14);
}
.filter_btn {
  display: flex;
  justify-content: flex-end;
  padding-left: 52px;
  margin-top: 13px;
}
.filter_btn > div {
  margin-left: 30px;
}
.table {
  flex: 1;
}
</style>