<template>
    <div class="text-center my-2 text-xl">
        <h2>Todo Application</h2>
    </div>
    <div class="flex justify-center my-5">
        <input type="text" placeholder="add your task" class="px-5 py-3 border mr-5">
        <button class="bg-green-950 text-neutral-50 px-5 py-3">Add</button>
    </div>
    <div class="flex justify-center my-7">
        <table>
        <thead class="bg-gray-50 border-b-2">
            <tr>
            <th class="p-3 tracking-wide font-semibold text-lg">Song</th>
            <th class="p-3 tracking-wide font-semibold text-lg">Artist</th>
            <th class="p-3 tracking-wide font-semibold text-lg">Year</th>
            </tr>
        </thead>
        <tbody>
            <tr>
            <td class="p-5 text-sm border">The Sliding</td>
            <td class="p-5 text-sm border">Malcolm Lockyer</td>
            <td class="p-5 text-sm border">1961</td>
            </tr>
            <tr>
            <td class="p-5 text-sm border">Witchy Woman</td>
            <td class="p-5 text-sm border">The Eagles</td>
            <td class="p-5 text-sm border">1972</td>
            </tr>
            <tr>
            <td class="p-5 text-sm border">Shining Star</td>
            <td class="p-5 text-sm border">Earth, Wind, and Fire</td>
            <td class="p-5 text-sm border">1975</td>
            </tr>
        </tbody>
        </table>
    </div>
</template>

<script setup>

</script>