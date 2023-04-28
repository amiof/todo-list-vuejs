<template>
    <div class="card">
        {{ task.title }}
        <div>

            <span class="material-symbols-outlined done">
                done
            </span>
            <span class="material-symbols-outlined edit">
                edit
            </span>
            <span class="material-symbols-outlined delete">
                delete
            </span>
        </div>
    </div>
</template>

<script>

export default {
    props: ["task"],
    methods: {
    },
}
</script>

<style  scoped>
.card {
    padding: 25px;
    background-color: #e7e8e5;
    /* border: 1px solid black; */
    border-radius: 10px;
    margin-top: 30px;
    display: flex;
    justify-content: space-between;


}

.card span {
    cursor: pointer;
    color: #aeafad;
}

.delete:hover {
    color: red
}

.edit:hover {
    color: blue;
}

.done:hover {
    color: green;
}
</style>

