<template>
    <div>
        <div>
            {{film.id}}
        </div>
    </div>
</template>

<script>
import films from "@/components/movies"
export default {
    data(){
        return{
            film:null
        }
    },
    created(){
       
        const film = films.find(film => film.id == $router.params.id)
        
        if(film){
            this.film = film
        }
        
        console.log(this.film)
    }
}
</script>

