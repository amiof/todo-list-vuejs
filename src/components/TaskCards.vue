<template>
    <div class="card" :class="{complate:task.complated}">
        <div @click="showDetails" class="task" >
            {{ task.title }}
            <h3 class="h3" v-if="details">detailes</h3>
            <p v-if="details">{{ task.body }}</p>

        </div>
        <div class="icons">

            <span class="material-symbols-outlined done" @click="changeComplate" >
                done
            </span>
            <span class="material-symbols-outlined edit">
                edit
            </span>
            <span class="material-symbols-outlined delete" @click="removeHandler">
                delete
            </span>
        </div>
    </div>
</template>

<script>

export default {
    props: ["task"],
    data() {
        return {
            url: "http://localhost:3000/posts/" + this.task.id,
            details: false,
            Complate: this.task.complated,
        }
    },
    methods: {
        showDetails() {
            return this.details = !this.details
        },
        changeComplate() {
            fetch(this.url, {
                method: "PATCH",
                headers: { "content-type": "application/json" },
                body: JSON.stringify({ complated: !this.task.complated })

            }).then(()=>this.$emit("RefreshDone",this.task.id))
                .catch(error => console.log(error))

        },
        removeHandler(){
            fetch(this.url,{method:"DELETE"})
                .then(()=>this.$emit("remove",this.task.id))
                .catch(error=>console.log(error))
        }
    },
}
</script>
k
<style  scoped>
.card {
    padding: 25px;
    background-color: #e7e8e5;
    /* border: 1px solid black; */
    border-radius: 10px;
    margin-top: 30px;
    display: flex;
    justify-content: space-between;
    border-left: 4px solid red;

}

.card.complate {
    border-left: 4px solid green;
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

.task {
    text-align: start;

}

.task p {
    margin-top: 5px;
}

.h3 {
    color: #aeafad;
    margin-top: 30px;
}

.icons {
    margin-right: 20px;
}
</style>

