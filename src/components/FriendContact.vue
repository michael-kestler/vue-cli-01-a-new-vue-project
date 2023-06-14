<template>
<li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : ''}}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show'}} Details</button>
    <ul v-if="detailsAreVisible">
        <li><strong>Phone: </strong> {{ phoneNumber }}</li>
        <li><strong>Email: </strong>{{ emailAddress }}</li>
    </ul>
</li>
</template>

<script>
    export default {
        // props: ['name', 'phoneNumber', 'emailAddress', 'isFavorite']
     props: {
        id: {
            type: String,
            required: true
        },
        name: {
            type: String,
            required: true
        },
        phoneNumber: {
            type: String,
            required: true
        }, 
        emailAddress: {
            type: String,
            required: true
            },
        isFavorite: {
            type: Boolean,
            required: false,
            default: false
            // validator: function(value){
            //     return value === '1' || value === '0';
            // }
        }
           
     },
     
    emits:['toggle-favorite'],

     //emits is the counterpart to props, in props you define which props this componenent receives in emits you define which custom events your component will emit 
     //this is useful for documentation so that collaborators don't have to read through all code to find events
    //  emits: {
    //     'toggle-favorite': function(id) {
    //         if (id){
    //             return true;
    //         } else {
    //             console.warn('Id is missing!');
    //             return false;
    //         }
    //     }
    //  },


    data(){
        return{
        detailsAreVisible: false,

        }
        
           
       
        
        },
        methods: {
            toggleDetails(){
                this.detailsAreVisible = !this.detailsAreVisible;
            },
            toggleFavorite(){
              this.$emit('toggle-favorite', this.id);
            }
        }
    }

</script>


