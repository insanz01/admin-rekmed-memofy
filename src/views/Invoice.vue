<!-- eslint-disable -->
<template>
  <div class="invoice">
    <!-- Sidebar -->
    <SidebarNav />
    <div id="content">
      <div class="card p-4">
        <div class="row">
          <div class="col-md-6">
            <div>
              <table class="table table-sm table-borderless">
                <tbody>
                  <tr>
                    <th>Nama</th>
                    <td>: {{ pasien_rekmed.nama }}</td>
                  </tr>
                  <tr>
                    <th>Nomor Rekam Medis</th>
                    <td>: {{ pasien_rekmed.ID }}</td>
                  </tr>
                  <tr>
                    <th>Status BPJS</th>
                    <td>: Tidak</td>
                  </tr>
                  <tr>
                    <th>Tanggal</th>
                    <td>: {{ pasien_rekmed.created_at }}</td>
                  </tr>
                </tbody>
              </table>
            </div>
            <div>
              <div class="card p-4">
                <div class="row my-3">
                  <div class="col-1">
                    <span>S</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-10">
                    <div v-for="(sub) in subjektif" v-bind:key="sub.id">
                      <span>{{ sub.nama }}</span><br>
                    </div>
                  </div>
                </div>
                <div class="row my-3">
                  <div class="col-1">
                    <span>O</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-10">
                    <div v-for="(obj) in objektif" v-bind:key="obj.id">
                      <div class="row">
                        <div class="col-5">Nadi</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.nadi }} x/min</div>
                      </div>
                      <div class="row">
                        <div class="col-5">Tekanan Darah</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.tekanan_darah }} mmHg</div>
                      </div>
                      <div class="row">
                        <div class="col-5">Suhu Tubuh</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.suhu_tubuh }} °C</div>
                      </div>
                      <div class="row">
                        <div class="col-5">Respirator Rate</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.respirator_rate }} x/min</div>
                      </div>
                      <div class="row">
                        <div class="col-5">Berat Badan</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.berat_badan }} kg</div>
                      </div>
                      <div class="row">
                        <div class="col-5">Tinggi Badan</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.tinggi_badan }} cm</div>
                      </div>
                      <div class="row">
                        <div class="col-5">Hasil Pemeriksaan</div>
                        <div class="col-1">:</div>
                        <div class="col-6">{{ obj.hasil_pemeriksaan }}</div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="row my-3">
                  <div class="col-1">
                    <span>A</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-10">
                    <div v-for="(ass) in assesment" v-bind:key="ass.id">
                      <span>{{ ass.nama_diagnosis }}</span>
                    </div>
                  </div>
                </div>
                <div class="row my-3">
                  <div class="col-1">
                    <span>P</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-10">
                    <div class="row">
                      <div class="col-5">Diagnostik</div>
                      <div class="col-1">:</div>
                      <div class="col-6">
                        <div v-for="plan1 in plan_diagnosis" v-bind:key="plan1.id">
                          <span>{{ plan1.nama_diagnosis }}</span><br>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-5">Terapi</div>
                      <div class="col-1">:</div>
                      <div class="col-6">
                        <div v-for="plan2 in plan_terapi" v-bind:key="plan2.id">
                          <span>{{ plan2.nama_terapi }}</span><br>
                        </div>
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-5">Edukasi</div>
                      <div class="col-1">:</div>
                      <div class="col-6">
                        <div v-for="plan3 in plan_edukasi" v-bind:key="plan3.id">
                          <span>{{ plan3.nama_edukasi }}</span><br>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="row my-3">
                  <div class="col-1">
                    <span>D</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-10">
                    <div v-for="(diagnosis) in diagnosis" v-bind:key="diagnosis.id">
                      <span>{{ diagnosis.nama }}</span>
                    </div>
                  </div>
                </div>
                <div class="row my-3">
                  <div class="col-1">
                    <span>T</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-10">
                    <div v-for="(tindakan) in tindakan" v-bind:key="tindakan.id">
                      <span>{{ tindakan.nama_tindakan }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md-6" id="invoice-payment">
            <div>
              <p class="h4 font-weight-bold text-center">Klink Citra Medika</p>
              <hr>
            </div>
            <div>
              <table class="table table-sm table-borderless">
                <tbody>
                  <tr>
                    <th>Nama</th>
                    <td>: {{ pasien_rekmed.nama }}</td>
                  </tr>
                  <tr>
                    <th>Nomor Rekam Medis</th>
                    <td>: {{ pasien_rekmed.ID }}</td>
                  </tr>
                </tbody>
              </table>
              <hr>
              <div v-for="obat in obat" v-bind:key="obat.id">
                <div class="row my-3">
                  <div class="col-2">
                    <span>R /</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-9">
                    <span class="my-3">{{ obat.nama_obat }}, {{ obat.jumlah }}</span><br>
                    <span> {{ obat.signa }} </span>
                  </div>
                </div>
              </div>
              <div v-for="racikan in tampil_racikan" v-bind:key="racikan.id">
                <div class="row my-3">
                  <div class="col-2">
                    <span>R /</span>
                  </div>
                  <div class="col-1">:</div>
                  <div class="col-9">
                    <div v-for="rac_obat in racikan.obat" v-bind:key="rac_obat.id">
                      <span class="my-3">{{ rac_obat.nama_obat }}, {{ rac_obat.jumlah }}</span><br>
                    </div>
                    <span>{{ racikan.pulv }}, {{ racikan.signa }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="row my-3">
        <div class="col col-lg-5">
        </div>
        <div class="col col-lg-3">
          <!-- <button type="button" @click="SimpanDenganResep()" class="btn btn-success btn-block float-right">Tambah Resep</button> -->
        </div>
        <div class="col col-lg-3">
          <button type="button" class="btn btn-primary float-right" onclick="window.print();">Cetak invoice</button>
        </div>
        <div class="col col-lg-1">
          <button type="button" class="btn btn-info float-right" @click="tambahTindakan()">Selesai</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
/*eslint-disable*/
// @ is an alias to /src
import SidebarNav from '@/components/SidebarNav.vue'
import axios from "axios"

  export default {
    name: 'invoice',
    components: {
      SidebarNav
    },
    data() {
      return {
        pasien_rekmed: [],
        subjektif: [],
        objektif: [],
        assesment: [],
        ass : [],
        plan_diagnosis: [],
        plan_terapi: [],
        plan_edukasi: [],
        tampil_racikan: [],
        racikan_obat: [],
        obat: [],
        diagnosis: [],
        tindakan: [],
        
      }
    },
    async created() {
      //localStorage.clear();
      const getData = (x) => {
        let y = localStorage.getItem(x);
        return JSON.parse(y) || [];
      }
      this.pasien_rekmed = getData('pasien');
      this.subjektif = getData('subjective');
      this.objektif = getData('objektive');
      this.assesment = getData('assesment');
      this.plan_diagnosis = getData('plan_diagnosis');
      this.plan_terapi = getData('plan_terapi');
      this.plan_edukasi = getData('plan_edukasi');
      this.tampil_racikan = getData('racikan');
      this.diagnosis = getData('diagnosis');
      this.tindakan = getData('tindakan');
      //this.racikan_obat = getData('racikan_obat')
      this.obat = getData('obat');

      //console.log('plan_diagnosis', this.plan_diagnosis)
      //console.log('assesment', this.assesment)
      /*console.log('pasien', this.pasien_rekmed)
      console.log('subjektif', this.subjektif)
      console.log('objektif', this.objektif)
      console.log('plan_terapi', this.plan_terapi)
      console.log('plan_edukasi', this.plan_edukasi)
      console.log('racikan', this.tampil_racikan)
      //console.log('racikan obat', this.racikan_obat)
      console.log('obat', this.obat)*/
      //console.log('diagnosis', this.diagnosis)
    },
    methods : {
      async tambahSubjektif() {
        for (var i = this.subjektif.length - 1; i >= 0; i--) {
          //console.log('subjektif',this.subjektif[i].nama)
          const sub = await axios.post('http://localhost/rekmed-server/Api/v1/Subjektif/post',{
            nama : this.subjektif[i].nama,
            ID_pasien : this.subjektif[i].ID_pasien
          }).then(res => this.sub = res.data)
        }
      },
      async tambahObjektif() {
        for (var i = this.objektif.length - 1; i >= 0; i--) {
          //console.log('objektif', this.objektif[i].nadi)
          const obj = await axios.post('http://localhost/rekmed-server/Api/v1/Objektif/post',{
            nadi : this.objektif[i].nadi,
            tekanan_darah : this.objektif[i].tekanan_darah,
            suhu_tubuh : this.objektif[i].suhu_tubuh,
            respiration_rate : this.objektif[i].respirator_rate,
            berat_badan : this.objektif[i].berat_badan,
            tinggi_badan : this.objektif[i].tinggi_badan,
            hasil_pemeriksaan : this.objektif[i].hasil_pemeriksaan,
            ID_pasien : this.pasien_rekmed.ID
          }).then(res => this.obj = res.data)
        }
      },
      async tambahAssesment() {
        for (var i = this.assesment.length - 1; i >= 0; i--) {
          const asses = await axios.post('http://localhost/rekmed-server/Api/v1/Assesment_terpilih/post',{
            nama_diagnosis : this.assesment[i].nama_diagnosis,
            ID_pasien : this.assesment[i].ID_pasien,
          }).then(res => this.asses = res.data)
          
          const tampil = await axios.get('http://localhost/rekmed-server/Api/v1/Assesment/get').then(res => res.data)
          this.ass = tampil
          //console.log(this.ass.value)
          let ada = false

          for (var a = this.ass.length - 1; a >= 0; a--) {
            //console.log('nama', this.ass[a].value)
            if(this.assesment[i].nama_diagnosis == this.ass[a].value) {
              //console.log('data sama', this.ass[a].value)
              ada = true
              break;
            }
          }
          if(ada){
            console.log('sama')
          } else {
            console.log('tidak')
            const simpan_ass = await axios.post('http://localhost/rekmed-server/Api/v1/Assesment/post',{
              value : this.assesment[i].nama_diagnosis
            }).then(res => this.simpan_ass = res.data)
            //console.log('tidak sama', this.ass[a].value)
          }
        }
      },
      async tambahDiagnosis() {
        for (var i = this.diagnosis.length - 1; i >= 0; i--) {
          const diag = await axios.post('http://localhost/rekmed-server/Api/v1/Diagnosis/post',{
            ID_pasien : this.diagnosis[i].ID_pasien,
            diagnosis : this.diagnosis[i].nama
          }).then(res => this.diag = res.data)
        }
      },
      async tambahTindakan() {
        for (var i = this.tindakan.length - 1; i >= 0; i--) {
          const tind = await axios.post('http://localhost/rekmed-server/Api/v1/Tindakan/post',{
            ID_pasien : this.tindakan[i].ID_pasien,
            tindakan : this.tindakan[i].nama_tindakan
          }).then(res => this.tind = res.data)
        }
      },
      selesai() {
      //post subjektif

      //localStorage.clear();
      } 
    }
  }

</script>
<style>
@media print {
    body * {
      visibility: hidden;
    }
    #invoice-payment, #invoice-payment * {
      visibility: visible;
    }
    #invoice-payment {
      /* position: absolute; */
      right: 300px;
      top: 270px;
      transform: scale(1.9);
      /* zoom: 100%; */
    }
  }
</style>