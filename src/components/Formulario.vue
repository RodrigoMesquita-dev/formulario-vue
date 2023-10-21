<template>
    <div class="container">
        <div class="row">
            <div class="col-6 bg-light">
                <span class="fs-4">ENTRADA DE DADOS</span>
                <hr>
                <!--<form @submit.prevent="enviar($event)">-->
                <form @reset.prevent="resetar()">
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Nome:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-model.lazy.trim="form.nome">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">E-mail:</label>
                        <div class="col">
                            <input type="email" class="form-control" v-model="form.email">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Senha:</label>
                        <div class="col">
                            <input type="password" class="form-control" v-model.trim="form.senha">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Idade:</label>
                        <div class="col">
                            <input type="number" class="form-control" v-model="form.idade">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Gênero:</label>
                        <div class="col">
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="Feminino" v-model="form.genero">
                                <label class="form-check-label">
                                    Feminino
                                </label>
                            </div>
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="Masculino" v-model="form.genero">
                                <label class="form-check-label">
                                    Masculino
                                </label>
                            </div>
                        </div>
                    </div>

                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Licença:</label>
                        <div class="col">
                            <div class="form-check form-switch">
                                <input
                                    class="form-check-input"
                                    type="checkbox"
                                    v-model="form.licensa"
                                    true-value="SIM"
                                    false-value="NÃO">
                                <label class="form-check-label">Li e aceito os termos</label>
                            </div>
                        </div>
                    </div>

                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Interesses:</label>
                        <div class="col">
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="Javascript" v-model="form.interesses">
                                <label class="form-check-label">
                                    JavaScript
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="VueJS" v-model="form.interesses">
                                <label class="form-check-label">
                                    VueJS
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="Angular" v-model="form.interesses">
                                <label class="form-check-label">
                                    Angular
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="NodeJS" v-model="form.interesses">
                                <label class="form-check-label">
                                    NodeJS
                                </label>
                            </div>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Telefone:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="(##) #####-####" v-model="form.telefone">
                            <small class="text-muted">Formato: 11 97777-5555</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">CEP::</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="#####-###" v-model="form.cep">
                            <small class="text-muted">Formato: 00000-000</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">CPF:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="###.###.###-##" v-model="form.cpf">
                            <small class="text-muted">Formato: 000.000.000-00</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">CNPJ:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="##.###.###/####-##" v-model="form.cnpj">
                            <small class="text-muted">Formato: 00.000.000/0000-00</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Cartão de crédito:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="#### #### #### ####" v-model="form.cartaoCredito">
                            <small class="text-muted">Formato: 0000 0000 0000 0000</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Placa veículo:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="AAA-####" data-maska-tokens="A:[A-Z]" data-maska-eager v-model="form.placaVeiculo">
                            <small class="text-muted">Formato: AAA-0000</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Placa veículo mercosul:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="AAA#A##" data-maska-tokens="A:[A-Z]" data-maska-eager v-model="form.placaVeiculoMercosul">
                            <small class="text-muted">Formato: AAA0A00</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">RG:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-maska data-maska="N-X" data-maska-tokens="X:[A-Z0-9]|N:[0-9]:multiple" data-maska-eager v-model="form.rg">
                            <small class="text-muted">Formato: Sem padrão</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Data:</label>
                        <div class="col">
                            <input type="date" class="form-control" v-model="form.data">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Data/hora local:</label>
                        <div class="col">
                            <input type="datetime-local" class="form-control" v-model="form.dataHoraLocal">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Mês:</label>
                        <div class="col">
                            <input type="month" class="form-control" v-model="form.mes">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Semana:</label>
                        <div class="col">
                            <input type="week" class="form-control" v-model="form.semana">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Hora:</label>
                        <div class="col">
                            <input type="time" class="form-control" v-model="form.hora">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Cor:</label>
                        <div class="col">
                            <input type="color" class="form-color" v-model="form.cor">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Valor limite:</label>
                        <div class="col">
                            <input type="range" class="form-range" min="0" max="100" step="1" v-model="form.alcance">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Escondido:</label>
                        <div class="col">
                            <input type="hidden" class="form-control" v-model="form.escondido">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Upload:</label>
                        <div class="col">
                            <input type="file" class="form-control" multiple @change="selecionarArquivos($event)">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Descrição:</label>
                        <div class="col">
                            <textarea class="form-control" rows="3" v-model="form.descricao"></textarea>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Cursos:</label>
                        <div class="col">
                            <select class="form-select" v-model="form.curso">
                                <option value="" disabled> -- Selecione uma opção --</option> <!-- É uma boa prática deixar uma opção disabled default de placeholder pra evitar incompatibilidades e conflitos-->
                                <option v-for="curso in cursos" :value="curso.id" :key="curso.id">{{ curso.id }} - {{ curso.curso }}</option>
                            </select>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Avaliação:</label>
                        <div class="col">
                            <input-estrelas :numero-estrelas="5" />
                        </div>  
                    </div>
                    <hr>
                    <div class="mb-3 row">
                        <div class="col d-flex justify-content-between">
                            <button class="btn btn-secondary" type="reset">Limpar</button>
                            <!--
                                este evento não será do tipo submit e sim do tipo click
                            -->
                            <button class="btn btn-success" type="button" @click="enviar()">Enviar (btn)</button>
                             <!-- se o submit estiver dentro de uma tag form o formulário em si é disparado e o submit é exec, no submit é feito um refresh da página,
                                pra previnir de dar refresh podemos usar o modificador prevent-->
                            <button class="btn btn-success" type="submit">Enviar (submit)</button>
                        </div>                        
                    </div>
                   
                </form>
            </div>

            
            <div class="col-6 text-white bg-secondary" :style="'background-color:'+form.cor+'!important'">
                <span class="fs-4">ESTADO DO OBJETO</span>
                <hr>
                <div class="mb-5 row">
                    <span>Estado do objeto</span>
                </div>

                <span class="fs-4">SAÍDA DE DADOS</span>
                <hr>
                <div class="mb-3 row">
                    <span>Nome: {{ form.nome }}</span>
                </div>
                <div class="mb-3 row">
                    <span>E-mail: {{ form.email }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Senha: {{ form.senha }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Idade: {{ form.idade }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Gênero: {{ form.genero }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Licença: {{ form.licensa }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Interesses:</span>
                    <ul>
                        <li v-for="(interesse, index) in form.interesses" :key="index" >{{interesse}}</li>
                    </ul>
                </div>
                <div class="mb-3 row">
                    <span>Telefone: {{ form.telefone }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Cep: {{ form.cep }}</span>
                </div>
                <div class="mb-3 row">
                    <span>CPF: {{ form.cpf }}</span>
                </div>
                <div class="mb-3 row">
                    <span>CNPJ: {{ form.cnpj }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Cartão de crédito: {{ form.cartaoCredito }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Placa veículo: {{ form.placaVeiculo }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Data: {{ $moment(form.data).format('YYYY/MM/DD') }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Data/hora local: {{ form.dataHoraLocal }}</span>
                    <ul>
                        <li> dia: {{ $moment(form.dataHoraLocal).format('dddd') }}</li>
                        <li> dia: {{ $moment(form.dataHoraLocal).add(10,'day') }}</li>
                        <li> dia: {{ $moment(form.dataHoraLocal).add(1,'month') }}</li>
                        <li> dia: {{ $moment(form.dataHoraLocal).add(2,'years') }}</li>
                    </ul>
                </div>
                <div class="mb-3 row">
                    <span>Mês: {{ form.mes }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Semana: {{ form.semana }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Hora: {{ form.hora }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Cor: {{ form.cor }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Valor limite: {{ form.alcance }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Escondido: {{ form.escondido }}</span>
                </div>
                <div class="mb-3 row">
                    <span>Upload:</span>
                    <ul>
                        <li v-for="(arquivo, index) in form.arquivos" :key="index" >{{ arquivo.name }}</li>
                    </ul>
                </div>
                <div class="mb-3 row">
                    <span>Descrição:</span>
                    <!--<pre>{{ form.descricao }}</pre>-->
                    <div style="white-space: pre;">{{ form.descricao }}</div>
                </div>
                <div class="mb-3 row">
                    <span>Curso: {{ form.curso }}</span>
                </div>
            </div>
        </div>

    </div>

</template>

<script>

import { vMaska } from "maska";
import InputEstrelas from "./InputEstrelas.vue";

export default {
    // eslint-disable-next-line
    name: 'Formulario',
    directives: { maska: vMaska },
    components: {
        InputEstrelas,
    },
    data: () => ({
        moment: {},
        cursos: [
            { id: 1, curso: 'Bancos de Dados Relacionais' },
            { id: 2, curso: 'Desenvolvimento web avançado com vue' },
            { id: 3, curso: 'Desenvolvimento web avançado com Laravel' },
            { id: 4, curso: 'Curso completo do desenvolvedor Node js e mongo DB' },
        ],
        form: {},
        formEstadoInicial: {
            nome: '',
            email: '',
            senha: '',
            idade: '',
            licensa: 'NÃO',
            interesses: [],
            genero: '',
            telefone: '',
            cep: '',
            cpf: '',
            cnpj: '',
            cartaoCredito: '',
            placaVeiculo: '',
            placaVeiculoMercosul: '',
            rg: '',
            data: '',
            dataHoraLocal: '',
            mes: '',
            semana: '',
            hora: '',
            cor: '#6c757d',
            alcance: 0,
            escondido: 'Esse input está escondido',
            arquivos: {},
            descricao: '',
            curso: '', // da maneira que programamos podemos colocar o valor 2 e o vue vai selecionar aquele option na tela
        }
    }),
    methods:{
        selecionarArquivos(event) {
            // console.log(event.target.files);
            this.form.arquivos = event.target.files;
        },
        enviar() {
            // normalmente quando estamos trabalhando com o envio de um form é interessante criar uma variável
            // que vai receber uma cópia do objeto original 
            // assim garantimos a integridade do objeto original
            const formEnvio = Object.assign({}, this.form);

            console.log(formEnvio);

            // uma requisição http para o backend.
        },
        resetar() {
            this.form = Object.assign({}, this.formEstadoInicial);
        }
    },
    created() {
        this.resetar();
    }
}
</script>
