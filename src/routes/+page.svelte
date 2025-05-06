<script lang="ts">
import "../css/app.css";
import Button from "../components/elements/Button.svelte";
import Input from "../components/elements/Input.svelte";
import PrioritySelect from "./prioritySelect.svelte";
import ToDoList from "./todoList.svelte";
import type { TODO } from "./types";

let title = $state("");
let priority = $state(0);
let todoList: TODO[] = $state([]);
let sortedTodoList = $derived(
  [...todoList].sort((item1, item2) => item1.priority - item2.priority),
);
let disabledCreateButton = $derived(title.length === 0);
const handleSend = () => {
  const newTodo: TODO = {
    title,
    priority,
    id: new Date().getTime(),
  };
  todoList.push(newTodo);
  title = "";
};
const deleteToDo = (id: number) => {
  todoList = todoList.filter((todo) => todo.id !== id);
};
</script>

<head>
    <title>ToDo-App</title>
</head>

<main class="prose mx-auto w-4/5 my-5">
    <h1>TODOアプリ</h1>
    <form>
        <Input label="Title" ID="titleInput" bind:value={title} className="my-3" />
        <PrioritySelect bind:priority={priority} className="my-3" />
        <Button text="作成" onClick={handleSend} className="my-3" disabled={disabledCreateButton} />
    </form>
    <ToDoList todoList={sortedTodoList} deleteToDo={deleteToDo} />
</main>
