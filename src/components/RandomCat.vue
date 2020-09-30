<template>

    <div class="row d-flex justify-content-center">
        <div class="col-md-12   ">
        <h1 class="text-center mt-5 mb-5"> Random Gif Cat</h1>
        </div>
        <div class="col-md-6">
            <div id="form">
                <div id="card">
                        <div class="form-group">
                            <label>Titulo:</label>
                            
                            <input type="text" class="form-control" v-model="tittle" ref="titulo">
                            
                        </div>
                        <div class="form-group">
                            <label>Filtro:</label>
                            <select id="inputState" class="custom-select" @change="changeFilter($event)">
                                <option v-for="opt in filtros" :key="opt" :value="opt" v-text="opt"></option>
                            </select>
                        </div>
                            <div class="form-group ">
                                <label>Color:</label>
                                
                                    <div class="input-group">
                                <select id="inputState" class="custom-select" @change="changeColor($event)">
                                    <option v-for="color in colors" :key="color.color" :value="color.value" v-text="color.color"></option>
                                </select>
                                <div class="input-group-prepend">
                                    <label class="input-group-text color-show" :style="style"></label>
                                </div>
                                </div>
                            </div>
                            <div class="form-group">
                                <label >Tamaño (px):</label>
                               
                                <input type="text" class="form-control" v-model="size" ref="size">
                                
                            </div>
                </div>
            </div>
            <a href="#" class="btn btn-primary btn-lg" @click="GetMyCat">Give my kitty!!</a>
        <div class="col">
            <img :src="url" class="img-fluid mt-5 mb-5">
        </div>
        </div>

</div>
</template>

<script>
export default {
    name: 'randomcat',
    // props: {},
    data: function () {
        return {
            tittle: "",
            size: "",
            myFilter: {
                filter: "",
            },
            filtros: [
                "blur",
                "mono",
                "negative",
                "paint",
                "sepia",
            ],
            selected: "",
            url: "",
            colors: [{
                    color: "Blanco",
                    value: "white"
                },
                {
                    color: "Verde",
                    value: "green"
                },
                {
                    color: "Rojo",
                    value: "red"
                },
                {
                    color: "Azul",
                    value: "blue"
                },
                {
                    color: "Amarillo",
                    value: "yellow"
                },
                {
                    color: "Morado",
                    value: "purple"
                }

            ],
            style: {
                background: ""
            }
        }
    },
    // computed: {},
    methods: {
        changeFilter(e) {
            var response = e.target.value
            if (response === "blur") {
                this.selected = "blur"

                console.log(this.selected)
            } else if (response === "mono") {
                this.selected = "mono"

            } else if (response === "negative") {
                this.selected = "negative"

            } else if (response === "paint") {
                this.selected = "paint"

            } else if (response === "sepia") {
                this.selected = "sepia"

            }
            return
            selected, url
        },
        changeColor(e) {
            this.style.background = e.target.value
        },
        GetMyCat() {
            if (this.tittle === "") {
                alert("El gatito debe tener un mensaje de amor y paz, escríbelo.")
                this.$refs.titulo.focus()
            }
             else if (this.size > 400 || this.size < 1 || isNaN(this.size)) {
                alert("Ingrese un número entre 1 y 400")
                this.$refs.size.value = ""
                this.$refs.size.focus()
            } else
                this.url = `https://cataas.com/cat/gif/says/${this.tittle}?filter=${this.selected}&color=${this.style.background}&size=${this.size}&type=or`
        }
    },
    // components: {},
}
</script>

<style scoped>
    .color-show {
        padding: 0 20px;
    }
    button{
        width:200px;
        margin-left:40%;
        margin-top:20px;
        margin-bottom:20px;
    }
</style>
