<script setup>
    import { ref } from 'vue';

    let inputValue = ref("")
    let inputValueNum = ref("")
    let showPopvariable = ref(false)
    const resetInput = () => {
      inputValue = '';
      inputValueNum = '';
    };

    const todos = ref([
        {
            id : 1,
            task : "task 1",
            time : 60,
            status : true
        },
        {
            id : 2,
            task : "task 2",
            time : 70,
            status : false
        },
        {
            id : 3,
            task : "task 3",
            time : 80,
            status : false
        },
    ])

    function addTodo(){
        let con = confirm('are you want to add item')
        if(con){
            todos.value.push({
                task : inputValue,
                time : inputValueNum,
                status : false
            })
            resetInput()
            closePop()
        }
    }
    let removeTodo = (i)=> {;
        todos.value.splice(i,1)
        // resetInput()
    }
    let showPop = ()=>{
        showPopvariable.value = true
    }
    let closePop = ()=>{
        showPopvariable.value = false
    }

</script>

<template>

<!-- Main modal -->
<div v-show="showPopvariable" id="authentication-modal" tabindex="-1" aria-hidden="true" class="overflow-y-auto overflow-x-hidden fixed top-0 right-0 left-0 z-50 justify-center items-center w-full md:inset-0 h-[calc(100%-1rem)] max-h-full">
    <div class="relative p-4 w-full max-w-md max-h-full">
        <!-- Modal content -->
        <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
            <!-- Modal header -->
            <div class="flex items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600">
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                    add task to our platform
                </h3>
                <button @click="closePop" type="button" class="end-2.5 text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ms-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white" data-modal-hide="authentication-modal">
                    <svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"/>
                    </svg>
                    <span class="sr-only">Close modal</span>
                </button>
            </div>
            <!-- Modal body -->
            <div class="p-4 md:p-5">
                <form class="space-y-4" action="#">
                    <div>
                        <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Task Name</label>
                        <input v-model="inputValue" type="text" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white" placeholder="write down your task" required>
                    </div>
                    <div>
                        <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Task Time</label>
                        <input v-model="inputValueNum" type="number" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white" placeholder="write down your task time" required>
                    </div>
                    <button @click="addTodo" type="submit" class="w-full text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">push to your database</button>
                </form>
            </div>
        </div>
    </div>
</div> 


    <!-- END -->
    <div class="text-center my-2 text-xl">
        <h2>Todo Application</h2>
    </div>
    <div class="flex justify-center my-5">
        <button class="bg-green-950 text-neutral-50 px-5 py-3 flex justify-center align-middle" @click="showPop">
            <span class="text-lg">new task</span>
            <i class="material-symbols-outlined my-auto">
                add
            </i>
        </button>
    </div>
    <div class="flex justify-center my-7">
        <table class="shadow">
        <thead class="bg-gray-50 border-b-2">
            <tr>
            <th class="p-3 tracking-wide font-semibold text-lg">SL</th>
            <th class="p-3 tracking-wide font-semibold text-lg">Task</th>
            <th class="p-3 tracking-wide font-semibold text-lg">Complete time</th>
            <th class="p-3 tracking-wide font-semibold text-lg">Status</th>
            <th class="p-3 tracking-wide font-semibold text-lg">Action</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(todo,index) in todos" :key="todo.id">
            <td class="p-5 text-sm border text-center">{{ index+1 }}</td>
            <td class="p-5 text-sm border text-center">{{ todo.task }}</td>
            <td class="p-5 text-sm border text-center">{{ todo.time }}</td>
            <td v-text="todo.status === false ? 'Not Done' : 'Done'" class="p-5 text-sm border text-center"></td>
            <td class="p-5 text-sm border text-center">
                <button class="bg-red-950 text-neutral-50 px-1.5 py-1.5" @click="removeTodo(index)">
                    <i class="material-symbols-outlined">
                        delete_forever
                    </i>
                </button>
            </td>
            </tr>
            <tr v-if="todos.length < 1">
                <td colspan="5" class="p-5 text-sm text-rose-800 text-center">No Data Found</td>
            </tr>
        </tbody>
        </table>
    </div>
</template>