<template>
  <div>
      <div class="row mt-5">
        <div class="col-4">
            
        </div>
        <div class="col-4">
            <h3>Generate Keypair</h3>
        </div>
        <div class="col-4"></div>
      </div>

      <div v-show="!showKeyPair">

      <div class="row mt-3">
        <div class="col-4">
            
        </div>
        <div class="col-4">
          <button
            class="btn btn-primary mr-2"
            type="button"
            v-on:click="generateKeyPair()"
            name="Generate"
            value="Generate"
          >
            Generate Keypair
          </button>
        </div>
        <div class="col-4"></div>
      </div>
</div>



<div v-show="showKeyPair">


      <div class="row mt-5">
        <div class="col-4">
            
        </div>
        <div class="col-4">
            public address:
        </div>
        <div class="col-4"></div>
      </div>

      <div class="row mt-3">
        <div class="col-4">
            
        </div>
        <div class="col-4">
            {{publicKey}}
        </div>
        <div class="col-4"></div>
      </div>

      <div class="row mt-3">
        <div class="col-4">
            
        </div>
        <div class="col-4">
            secret key: 
        </div>
        <div class="col-4"></div>
      </div>

      <div class="row mt-3">
        <div class="col-4">
            
        </div>
        <div class="col-4">
            {{secretKey}}
        </div>
        <div class="col-4"></div>
      </div>

      <div class="row mt-3">
        <div class="col-4">
            
        </div>
        <div class="col-4">
                      <button
            class="btn btn-primary mr-2"
            type="button"
            v-on:click="reset()"
            name="Reset"
            value="Reset"
          >
            Reset Generator
          </button>
        </div>
        <div class="col-4"></div>
      </div>
</div>
     


  </div>
</template>

<script>
// @ is an alias to /src
import EthCrypto from "eth-crypto";

export default {
  name: "Home",
  components: {          
   
  },
    data() {
    return {
      publicKey: "",
      secretKey: "",
      showKeyPair: false
    };
  },

  methods: {
    generateKeyPair(){
        console.log("generate button pressed");

        const newKeyPair = EthCrypto.createIdentity();   

        console.log(
          `Address : ${newKeyPair.address}, privateKey: ${newKeyPair.privateKey}`
        );
        
        this.publicKey = newKeyPair.address;
        this.secretKey = newKeyPair.privateKey;
        this.showKeyPair = true;
    },
    reset(){
      console.log("reset button pressed");
      this.showKeyPair = false;
      this.publicKey = "";
      this.secretKey = "";
    }
  }

};
</script>
