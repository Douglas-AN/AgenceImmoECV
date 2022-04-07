<template>
  <div id="annonce">
    <div v-for="annonce in annonces" :key="annonce.id">
      <img src="../img.jpeg" alt="Image bien immo" />
      <h1>{{ annonce.attributes.Intitule }}</h1>
      <div class="info">
        <div class="first">
          <span class="piece">{{ annonce.attributes.Nombre_de_piece }} pièces</span>
          <span class="chambre">{{ annonce.attributes.Nombre_de_chambre }} chambres</span>
          <span class="surface">{{ annonce.attributes.Surface }} m2</span>
        </div>
        <span class="prix">{{ annonce.attributes.Prix }} €</span>
      </div>
      <div class="description">
          <h2>Description du professionnel</h2>
          <p>{{ annonce.attributes.Description }}</p>
      </div>
      <div class="caracteristique">
          <h2>Caractéristiques</h2>
          <p>Construit en {{ annonce.attributes.Annee_de_construction }}</p>
          <ul>
              <li>Nombre de pièces : {{ annonce.attributes.Nombre_de_piece }}</li>
              <li>Nombre de chambres :{{ annonce.attributes.Nombre_de_chambre }}</li>
              <li>Surface habitable : {{ annonce.attributes.Surface }}m2</li>
              <li>Surface du terrain :{{ annonce.attributes.Terrain }}m2</li>
          </ul>
      </div>
      <div class="chauffage">
          <h2>Chauffage et diagnostics</h2>
          <div class="dpe">
              <h3>Diagnostic de performance énergétique (DPE)</h3>
              <div class="diagnostic-bar">
                  <div class="diagnostic-bar">
                  <div class="jtAZeY"></div>
                  <div class="cHdwoA"></div>
                  <div class="erhoTN"></div>
                  <div class="gyFuZw">
                      <p>{{ annonce.attributes.Classe_energetique }}</p>
                  </div>
                  <div class="eNOvob"></div>
                  <div class="awgrA"></div>
                  <div class="kicGHR"></div>
              </div>
              </div>
          </div>
          <div class="ges">
              <h3>Indice d'émission de gaz à effet de serre (GES)</h3>
              <div class="diagnostic-bar">
                  <div class="cVeDfv"></div>
                  <div class="ckmPDS"></div>
                  <div class="DzsvH"></div>
                  <div class="bphHmi">
                      <p>{{ annonce.attributes.GES }}</p>
                  </div>
                  <div class="eZZiHV"></div>
                  <div class="eLnHlr"></div>
                  <div class="kWBKtj"></div>
              </div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Etablissements from "../components/Etablissements.vue";
export default {
  components: { Etablissements },
  name: "IndexPage",
  data() {
    return {
      annonces: [],
    };
  },
  async mounted() {
    this.$route.params.annonceId;
    const response = await axios({
      url: "http://localhost:1337/api/etablissements",
      method: "get",
    });
    this.annonces = response.data.data;
    console.log(this.annonces[0].attributes);
  },
};
</script>

<style>
#annonce {
  max-width: 80vw;
  margin: 0 auto;
}
img {
    width: 100%;
}
/* DPE CLASS **********************************************************/
/* GES CLASS **********************************************************/
.cVeDfv, .ckmPDS, .DzsvH, .bphHmi, .eZZiHV, .eLnHlr, .kWBKtj {
    display: inline-block;
    vertical-align: top;
    max-width: 46px;
    background-color: rgb(163, 219, 252);
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    color: rgb(0, 0, 0);
    margin-right: 1px;
    border: 1px solid rgb(255, 255, 255);
}
.cVeDfv{
    width: 13%;
    height: 12px;
    line-height: 12px;
    background-color: rgb(163, 219, 252);
    border-radius: 100px 0px 0px 100px;
    margin-right: 1px;
}
.ckmPDS{
    background-color: rgb(138, 181, 210);
    font-size: 16px;
    text-align: center;
    color: rgb(0, 0, 0);
    position: relative;
    width: 48px;
    height: 32px;
    margin-top: -10px;
    margin-left: -1px;
    margin-right: -1px;
    line-height: 28px;
    font-weight: bold;
    border: 2px solid rgb(255, 255, 255);
    border-radius: 4px;
}
.DzsvH{
    display: inline-block;
    vertical-align: top;
    width: 13%;
    max-width: 46px;
    height: 12px;
    line-height: 12px;
    background-color: rgb(118, 146, 177);
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    color: rgb(0, 0, 0);
    margin-right: 1px;
    border: 1px solid rgb(255, 255, 255);
}
.bphHmi{
    display: inline-block;
    vertical-align: top;
    width: 13%;
    max-width: 46px;
    height: 12px;
    line-height: 12px;
    background-color: rgb(94, 112, 141);
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    color: rgb(255, 255, 255);
    margin-right: 1px;
    border: 1px solid rgb(255, 255, 255);
}
.eZZiHV{
    display: inline-block;
    vertical-align: top;
    width: 13%;
    max-width: 46px;
    height: 12px;
    line-height: 12px;
    background-color: rgb(77, 82, 114);
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    color: rgb(255, 255, 255);
    margin-right: 1px;
    border: 1px solid rgb(255, 255, 255);
}
.eLnHlr{
    display: inline-block;
    vertical-align: top;
    width: 13%;
    max-width: 46px;
    height: 12px;
    line-height: 12px;
    background-color: rgb(57, 53, 80);
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    color: rgb(255, 255, 255);
    margin-right: 1px;
    border: 1px solid rgb(255, 255, 255);
}
.kWBKtj{
    display: inline-block;
    vertical-align: top;
    width: 13%;
    max-width: 46px;
    height: 12px;
    line-height: 12px;
    background-color: rgb(41, 27, 53);
    font-size: 16px;
    font-weight: bold;
    text-align: center;
    color: rgb(255, 255, 255);
    border-radius: 0px 100px 100px 0px;
    margin-right: 1px;
    border: 1px solid rgb(255, 255, 255);
}
</style>
