<template>
	<div class="container mt-5">
		<h1 class="text-center">Kanban Board With Vue</h1>
		<div class="row">
			<div class="col form-inline">
				<input
					v-model="newTask"
					class="task-input mb-5 mt-3"
					placeholder="Enter Task"
					@keyup.enter="add"
				/>
			</div>
		</div>

		<div class="row">
			<div class="col-md-3">
				<div class="p-2 alert alert-secondary">
					<h3>Backlog</h3>
					<hr />
					<draggable
						class="list-group kanban-board"
						:list="arrBackLog"
						group="tasks"
					>
						<template #item="{ element }">
							<li class="list-group-item">{{ element.name }}</li>
						</template>
					</draggable>
				</div>
			</div>

			<div class="col-md-3">
				<div class="p-2 alert alert-primary">
					<h3>In Progress</h3>
					<hr />
					<draggable
						class="list-group kanban-board"
						:list="arrInProgress"
						group="tasks"
					>
						<template #item="{ element }">
							<li class="list-group-item">{{ element.name }}</li>
						</template>
					</draggable>
				</div>
			</div>

			<div class="col-md-3">
				<div class="p-2 alert alert-warning">
					<h3>Testing</h3>
					<hr />
					<draggable
						class="list-group kanban-board"
						:list="arrTested"
						group="tasks"
					>
						<template #item="{ element }">
							<li class="list-group-item">{{ element.name }}</li>
						</template>
					</draggable>
				</div>
			</div>

			<div class="col-md-3">
				<div class="p-2 alert alert-success">
					<h3>Done</h3>
					<hr />
					<draggable
						class="list-group kanban-board"
						:list="arrDone"
						group="tasks"
					>
						<template #item="{ element }">
							<li class="list-group-item">{{ element.name }}</li>
						</template>
					</draggable>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import draggable from "vuedraggable";

export default {
	name: "App",
	components: {
		draggable,
	},
	data() {
		return {
			newTask: "",
			arrBackLog: [
				{ name: "Vue Kanban Board" },
				{ name: "PHP Learning" },
				{ name: "PHP Project" },
				{ name: "Vue Composition API" },
			],
			arrInProgress: [],
			arrTested: [],
			arrDone: [],
		};
	},
	methods: {
		add() {
			if (this.newTask) {
				this.arrBackLog.push({ name: this.newTask });
				this.newTask = "";
			}
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

.kanban-board {
	min-height: 300px;
}

li {
	margin: 5px;
	border-radius: 5px;
	cursor: pointer;
}

.task-input {
	padding: 7px;
	border-radius: 5px;
	border: 1px solid grey;
}
</style>
