<template>
  <q-page class="q-pa-md">
    
    
    <div class="row">
          <!-- ejercicio 1 -->
           <!-- ejercicio2 -->
         <div class="col-6">    
             <p>
               Se desea estimar la proporcion de amas de casa de una ciudad que prefieren consumir 
               el nuevo detergente BLANQUITO  <br>  con una confianza del 95% y un error del 5%, si  <br>
               a) No se conoce el tamaño de la población y no hay encuesta anterior
                </p> 
            <div class="row">             
                <div class="col-2">
                    <q-item>
                    <q-input
                        bottom-slots
                        dense
                        autogrow
                        outlined
                        class="full-width"
                        label="Z"
                        v-model="Z2"
                    >
                        <template v-slot:hint>
                        <q-badge outline color="secondary" label="confianza" />
                        </template>
                    </q-input>
                    </q-item>
                </div>
                <div class="col-2">
                    <q-item>
                    <q-input
                        bottom-slots
                        dense
                        autogrow
                        outlined
                        class="full-width"
                        label="d"
                        v-model="e"
                    >
                        <template v-slot:hint>
                        <q-badge outline color="secondary" label="error" />
                        </template>
                    </q-input>
                    </q-item>
                </div>
                <div class="col-2">
                    <q-item>
                    <q-input
                        bottom-slots
                        dense
                        autogrow
                        outlined
                        class="full-width"
                        label="p"
                        v-model="p2"
                    >
                        <template v-slot:hint>
                        <q-badge
                            outline
                            color="secondary"
                            label="Prevalencia del e."
                        />
                        </template>
                    </q-input>
                    </q-item>
                </div>               
                <div class="col-1">
                    <q-item>
                    <q-btn color="primary" label="Calcular" @click="calculate2" />
                    </q-item>
                </div>

            </div>        
            <br />

            <div class="row">
            <br />
             <div class="col-6">
                  <q-list bordered class="rounded-borders" style="max-width: 800px">
                <q-item-label header>Formula</q-item-label>
                <q-separator spaced />
                <q-item>
                <q-item-section avatar top> </q-item-section>
                <q-item-section top>
                    <q-item-label lines="1">
                    <center>                      
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ Z2 }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ p2 }}*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px">{{
                        q2
                        }}</span>
                    </center>
                    </q-item-label>
                    <q-item-label caption lines="1">
                    <hr />
                    </q-item-label>
                    <q-item-label lines="1">
                    <center>
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ e }}²</span>
                       
                    </center>
                    </q-item-label>
                </q-item-section>

                <q-item-section top side>
                    <div class="text-grey-8 q-gutter-xs">
                    <h6>={{ resultado2.toFixed(2) }}</h6>
                    </div>
                </q-item-section>
                </q-item>
                 </q-list>
                 </div>
                 
            </div>
            <div class="col-6">
                <br>
                <p>{{mensaje}}</p>
            </div>
        </div>
        <div class="col-6">    
             <p>
                b) En la ciudad hay 2500 familias y en un encuesta anterior solamente el 12 % de amas de casa manifestaron consumir el producto.
                </p> 
            <div class="row">
              <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    type="number"
                    label="N"
                    v-model.number="N"
                >
                    <template v-slot:hint>
                    <q-badge outline color="secondary" label="Total Poblacion" />
                    </template>
                </q-input>
                </q-item>
              </div>
               <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    label="Z"
                    v-model="Z"
                >
                    <template v-slot:hint>
                    <q-badge outline color="secondary" label="Confianza" />
                    </template>
                </q-input>
                </q-item>
            </div>
             <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    label="p"
                    v-model="p"
                >
                    <template v-slot:hint>
                    <q-badge
                        outline
                        color="secondary"
                        label="Prevalencia del e."
                    />
                    </template>
                </q-input>
                </q-item>
            </div>
               <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    label="E"
                    v-model="d"
                >
                    <template v-slot:hint>
                    <q-badge outline color="secondary" label="Error" />
                    </template>
                </q-input>
                </q-item>
            </div>
             <div class="col-1">
                <q-item>
                   <q-btn color="primary" label="Calcular" @click="calculate" />
                </q-item>
            </div>

            </div>        
            <br />
            <div class="row">
            <br />
             <div class="col-6">
            <q-list bordered class="rounded-borders" style="max-width: 700px">
                <q-item-label header>Formula</q-item-label>
                <q-separator spaced />
                <q-item>
                <q-item-section avatar top> </q-item-section>
                <q-item-section top>
                    <q-item-label lines="1">
                    <center>
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ N }}*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ Z }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ p }}*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px">{{
                        q
                        }}</span>
                    </center>
                    </q-item-label>
                    <q-item-label caption lines="1">
                    <hr />
                    </q-item-label>
                    <q-item-label lines="1">
                    <center>
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ d }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >({{ N }}-1)+</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ Z }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ p }}*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px">{{
                        q
                        }}</span>
                    </center>
                    </q-item-label>
                </q-item-section>

                <q-item-section top side>
                    <div class="text-grey-8 q-gutter-xs">
                    <h6>={{ resultado.toFixed(2) }}</h6>
                    </div>
                </q-item-section>
                </q-item>
            </q-list>
                 </div>
            </div>
             <div class="col-6">
                <br>
                <p>{{mensaje0}}</p>
            </div>
        </div>

        

    </div>
    <hr>

    <div class="row">
        <div class="col-6">
             <p>
                Se desa estimar el gasto promedio mensual en dolares que una famila de la ciudad de trujillo gasta en embutidos. <br>
                a). calcule cuantas familas se deben tomar como muestra con una confianza del 95%  y un error de 2 dolares. <br> Un especialista a estimado
                una desviacion estandar de 9 dolares
                </p> 
            <div class="row">                
                <div class="col-2">
                    <q-item>
                    <q-input
                        bottom-slots
                        dense
                        autogrow
                        outlined
                        class="full-width"
                        label="Z"
                        v-model="Z3"
                    >
                        <template v-slot:hint>
                        <q-badge outline color="secondary" label="confianza" />
                        </template>
                    </q-input>
                    </q-item>
                </div>
                <div class="col-2">
                    <q-item>
                    <q-input
                        bottom-slots
                        dense
                        autogrow
                        outlined
                        class="full-width"
                        label="error"
                        v-model="E2"
                    >
                        <template v-slot:hint>
                        <q-badge outline color="secondary" label="error" />
                        </template>
                    </q-input>
                    </q-item>
                </div>
                <div class="col-2">
                    <q-item>
                    <q-input
                        bottom-slots
                        dense
                        autogrow
                        outlined
                        class="full-width"
                        label="s"
                        v-model="S"
                    >
                        <template v-slot:hint>
                        <q-badge
                            outline
                            color="secondary"
                            label="varianza."
                        />
                        </template>
                    </q-input>
                    </q-item>
                </div>               
                <div class="col-1">
                    <q-item>
                    <q-btn color="primary" label="Calcular" @click="calculate3" />
                    </q-item>
                </div>
            </div>

            <div class="row">
            <br />
             <div class="col-6">
                  <q-list bordered class="rounded-borders" style="max-width: 700px">
                <q-item-label header>Formula</q-item-label>
                <q-separator spaced />
                <q-item>
                <q-item-section avatar top> </q-item-section>
                <q-item-section top>
                    <q-item-label lines="1">
                    <center>                      
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ Z3 }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ S }}²</span>                       
                    </center>
                    </q-item-label>
                    <q-item-label caption lines="1">
                    <hr />
                    </q-item-label>
                    <q-item-label lines="1">
                    <center>
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ E2 }}²</span>                       
                    </center>
                    </q-item-label>
                </q-item-section>
                <q-item-section top side>
                    <div class="text-grey-8 q-gutter-xs">
                    <h6>={{ resultado3.toFixed(2) }}</h6>
                    </div>
                </q-item-section>
                </q-item>
                 </q-list>
                 </div>                 
            </div>
            <div class="col-6">
                <br>
                <p>{{mensaje3}}</p>
            </div>
        </div>
        <div class="col-6">
            <p> b) Haga el calculo para una urbanizacion con 850 familias con un 99% de confianza y un error de 1.5 dolares  considerando la desviacion estandar con un valor de 9 dolares</p>
                 <div class="row">
              <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    type="number"
                    label="N"
                    v-model.number="N2"
                >
                    <template v-slot:hint>
                    <q-badge outline color="secondary" label="Total Poblacion" />
                    </template>
                </q-input>
                </q-item>
              </div>
               <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    label="Z"
                    v-model="Z4"
                >
                    <template v-slot:hint>
                    <q-badge outline color="secondary" label="Confianza" />
                    </template>
                </q-input>
                </q-item>
            </div>
             <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    label="S"
                    v-model="S2"
                >
                    <template v-slot:hint>
                    <q-badge
                        outline
                        color="secondary"
                        label="Varianza"
                    />
                    </template>
                </q-input>
                </q-item>
            </div>
               <div class="col-2">
                <q-item>
                <q-input
                    bottom-slots
                    dense
                    autogrow
                    outlined
                    class="full-width"
                    label="E"
                    v-model="E3"
                >
                    <template v-slot:hint>
                    <q-badge outline color="secondary" label="Error" />
                    </template>
                </q-input>
                </q-item>
            </div>
             <div class="col-1">
                <q-item>
                   <q-btn color="primary" label="Calcular" @click="calculate4" />
                </q-item>
            </div>

            </div>        
            <br />
            <div class="row">
            <br />
             <div class="col-6">
            <q-list bordered class="rounded-borders" style="max-width: 700px">
                <q-item-label header>Formula</q-item-label>
                <q-separator spaced />
                <q-item>
                <q-item-section avatar top> </q-item-section>
                <q-item-section top>
                    <q-item-label lines="1">
                    <center>
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ N2 }}*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ Z4 }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ S2 }}²</span
                        >
                        
                    </center>
                    </q-item-label>
                    <q-item-label caption lines="1">
                    <hr />
                    </q-item-label>
                    <q-item-label lines="1">
                    <center>
                       
                        <span class="text-weight-medium" style="font-size: 20px"
                        >({{ N2 }}-1)</span
                        >


                         <span class="text-weight-medium" style="font-size: 20px"
                        >{{ E3 }}²+</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ Z4 }}²*</span
                        >
                        <span class="text-weight-medium" style="font-size: 20px"
                        >{{ S2 }}²</span
                        >
                       
                    </center>
                    </q-item-label>
                </q-item-section>

                <q-item-section top side>
                    <div class="text-grey-8 q-gutter-xs">
                    <h6>={{ resultado4.toFixed(2) }}</h6>
                    </div>
                </q-item-section>
                </q-item>
            </q-list>
                 </div>
            </div>

        </div>



    </div>

  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "Ejercicios",
  data() {
    return {
      N: "N",
      Z: "Z",
      p: "p",
      q: "q",
      d: "d",
      re: 0,
      resultado: 0,
      mensaje0:'',


      Z2:'Z',
      p2:'p',
      q2:'q',
      e:'E',
      resultado2:0,
      mensaje:'',

      Z3:'Z',
      S:'S',
      E2:'E',
      resultado3:0,
      mensaje3:'',

      N2:'N2',
      Z4:'Z2',
      S2:'S2',
      E3:'E2',
      resultado4:0,
      mensaje4:'',
    };
  },
  mounted() {
   
  },
  methods: {
    init() {
      this.N = 15000;
      this.Z = Math.pow(1.96, 2).toFixed(4);
      this.p = 0.05;
      this.q = 0.95;
      this.d = Math.pow(0.03, 2).toFixed(4);
      this.re = this.N * parseFloat(this.Z) * this.p * this.q;
    
    },
    calculate() {  
      this.q = 1 - parseFloat(this.p);
      this.resultado =  (parseInt(this.N) * Math.pow(this.Z, 2).toFixed(4) * parseFloat(this.p) * this.q) /
                        (Math.pow(this.d, 2) * (this.N - 1) +  Math.pow(this.Z, 2).toFixed(4) * this.p * this.q);
      this.mensaje0="se debe tomar una muestra de "+ Math.round(this.resultado)+" amas de casa";;                  
    },
    calculate2(){
        this.q2 = 1 - parseFloat(this.p2);
        this.resultado2= (Math.pow(this.Z2,2)*this.p2*this.q2)/(Math.pow(this.e,2));             
        this.mensaje="se deberia tomar una muestra de "+ Math.round(this.resultado2)+" amas de casa";
    },
    calculate3() {
        this.resultado3= (Math.pow(this.Z3,2)* Math.pow(this.S,2))/( Math.pow(this.E2,2));
        this.mensaje3="si se desea estimar el gasto promedio mensual en dolares que una famila de  la ciudad de trujillo gasta en embutidos,se deberia tomar una muestra de "+ Math.round(this.resultado3)+" familas";
    },
    calculate4() {
        this.resultado4= ( this.N2* Math.pow(this.Z4,2)* Math.pow(this.S2,2)) / ( Math.pow(this.E3,2)  *(this.N2-1)+ Math.pow(this.Z4,2)*Math.pow(this.S2,2) );
        this.mensaje4="si se desea estimar el gasto   mensual  promedio que las familas de esta urbanizacion efectuan consumo de embutidos  mensualmente se deberia tomar una muestra de   "+ Math.round(this.resultado4)+" familas";
    }

  },
});
</script>
