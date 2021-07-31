<template>
    <div id="app">
        <div class="jumbotron jumbotron-fluid">
            <div class="container">
                <h1 class="display-4">Formulários no Vue</h1>
                <p class="lead">Treinando a manipulação de formulários</p>
            </div>
        </div>

        <div class="container">
            <div class="row">
                <!-- Formulário -->
                <div class="col-sm-6">
                    <h3>Preencha abaixo</h3>

                    <form @submit.prevent="enviar" @reset.prevent="resetar">
                        <!-- Nome -->
                        <div class="form-group">
                            <label>Nome:</label>
                            <input
                                type="text"
                                class="form-control"
                                placeholder="Seu nome"
                                v-model.lazy.trim="desenvolvedor.nome"
                            />
                        </div>

                        <!-- Email -->
                            <!-- v-model por baixo dos panos :D -->
                        <div class="form-group">
                            <label>Endereço de email:</label>
                            <!-- <input
                                type="email"
                                class="form-control"
                                placeholder="Seu email"
                                v-model.lazy.trim="desenvolvedor.email"
                            /> -->
                            <input
                                type="email"
                                class="form-control"
                                placeholder="Seu email"
                                :value="desenvolvedor.email"
                                @input="desenvolvedor.email = $event.target.value"
                            />
                        </div>

                        <!-- Idade -->
                        <div class="form-group">
                            <label>Idade:</label>
                            <input
                                type="number"
                                class="form-control"
                                placeholder="Sua idade"
                                min="1"
                                max="150"
                                v-model.number="desenvolvedor.idade"
                            />
                        </div>

                        <!-- Genero -->
                        <div class="form-group">
                            <p>Gênero:</p>

                            <div class="form-check form-check-inline">
                                <input
                                    type="radio"
                                    class="form-check-input"
                                    value="Masculino"
                                    id="masculino"
                                    v-model="desenvolvedor.genero"
                                />
                                <label class="form-check-label" for="masculino"
                                    >Masculino</label
                                >
                            </div>

                            <div class="form-check form-check-inline">
                                <input
                                    type="radio"
                                    class="form-check-input"
                                    value="Feminino"
                                    id="feminino"
                                    v-model="desenvolvedor.genero"
                                />
                                <label class="form-check-label" for="feminino"
                                    >Feminino</label
                                >
                            </div>
                        </div>

                        <!-- Ocupação -->
                        <div class="form-group">
                            <label>Ocupação:</label>
                            <select
                                class="form-control"
                                v-model="desenvolvedor.ocupacao"
                            >
                                <option value="" disabled>Selecione um opção...</option>
                                <option 
                                    v-for="(ocupacao, indice) in ocupacoes"
                                    :key="indice"
                                    :value="ocupacao"
                                >
                                    {{ ocupacao }}
                                </option>
                            </select>
                        </div>

                        <!-- Tecnologias -->
                        <div class="form-group">
                            <p>Tecnologias:</p>

                            <div class="form-check form-check-inline">
                                <input
                                    type="checkbox"
                                    class="form-check-input"
                                    value="Javascript"
                                    id="javascript"
                                    v-model="desenvolvedor.tecnologias"
                                />
                                <label class="form-check-label" for="javascript">
                                    Javascript
                                </label>
                            </div>

                            <div class="form-check form-check-inline">
                                <input
                                    type="checkbox"
                                    class="form-check-input"
                                    value="Vue JS"
                                    id="vuejs"
                                    v-model="desenvolvedor.tecnologias"
                                />
                                <label class="form-check-label" for="vuejs">
                                    Vue JS
                                </label>
                            </div>

                            <div class="form-check form-check-inline">
                                <input
                                    type="checkbox"
                                    class="form-check-input"
                                    value="Vuex"
                                    id="vuex"
                                    v-model="desenvolvedor.tecnologias"
                                />
                                <label class="form-check-label" for="vuex">
                                    Vuex    
                                </label>
                            </div>

                            <div class="form-check form-check-inline">
                                <input
                                    type="checkbox"
                                    class="form-check-input"
                                    value="Vue Router"
                                    id="vuerouter"
                                    v-model="desenvolvedor.tecnologias"
                                />
                                <label class="form-check-label" for="vuerouter">
                                    Vue Router
                                </label>
                            </div>
                        </div>

                        <!-- Biografia -->
                        <div class="form-group">
                            <label>Resumo de perfil:</label>
                            <textarea
                                class="form-control"
                                placeholder="Conte-nos um pouco sobre você..."
                                v-model="desenvolvedor.biografia"
                            ></textarea>
                        </div>

                        <!-- Salário -->
                        <div class="form-group">
                            <AppRange 
                                label="Salário pretendido:"
                                v-model.number="desenvolvedor.salario"
                                min="1000"
                                max="15000"
                                step="500"
                                inputClasses="form-control-range"
                            />
                        </div>

                        <!-- Notificacões -->
                        <div class="form-group">
                            <div class="form-check form-check-inline">
                                <input
                                    type="checkbox"
                                    class="form-check-input"
                                    v-model="desenvolvedor.notificacoes"
                                    true-value="Sim"
                                    false-value="Não"
                                />
                                <label class="form-check-label">
                                    Receber notificações por email
                                </label>
                            </div>
                        </div>

                        <button class="btn btn-secondary" type="reset">Resetar</button>
                        <!-- <button class="btn btn-success" type="button" @click="enviar">Enviar</button> -->
                        <button class="btn btn-success" type="submit">Enviar</button>
                    </form>
                </div>

                <!-- Output -->
                <div class="col-sm-6">
                    <h3>Saída</h3>

                    <div class="card">
                        <div class="card-header text-center">Dados</div>

                        <ul class="list-group list-group-flush">
                            <li class="list-group-item">
                                <strong>Nome:</strong>
                                {{ desenvolvedor.nome }}
                            </li>
                            <li class="list-group-item">
                                <strong>Email:</strong>
                                {{ desenvolvedor.email }}
                            </li>
                            <li class="list-group-item">
                                <strong>Idade:</strong>
                                {{ desenvolvedor.idade }}
                            </li>
                            <li class="list-group-item">
                                <strong>Gênero:</strong>
                                {{ desenvolvedor.genero }}
                            </li>
                            <li class="list-group-item">
                                <strong>Ocupação:</strong>
                                {{ desenvolvedor.ocupacao }}
                            </li>
                            <li class="list-group-item">
                                <strong>Tecnologias:</strong>
                                <ul>
                                    <li 
                                        v-for="(tecnologia, i) in desenvolvedor.tecnologias"
                                        :key="i"
                                    >
                                        {{ tecnologia }}
                                    </li>
                                </ul>
                            </li>
                            <li class="list-group-item">
                                <strong>Biografia:</strong>
                                <pre>{{ desenvolvedor.biografia }}</pre>
                            </li>
                            <li class="list-group-item">
                                <strong>Receber notificações?</strong>
                                {{ desenvolvedor.notificacoes }}
                            </li>
                            <li class="list-group-item">
                                <strong>Salário pretendido:</strong>
                                R$ {{ desenvolvedor.salario }}
                            </li>
                        </ul>

                        <div class="card-header">Model</div>

                        <div class="card-body">
                            <pre><code>{{ desenvolvedor }}</code></pre>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import AppRange from './components/Range'

export default {
    components: {
        AppRange
    },

    data: () => ({
        valoresPadrão: {
            nome: 'Matheus',
            email: 'matttalves@gmail.com',
            idade: 24,
            biografia: 'Dev in-progress',
            genero: 'Masculino',
            ocupacao: '',
            tecnologias: ['Javascript'],
            notificacoes: 'Sim',
            salario: 2000
        },

        desenvolvedor: {},

        ocupacoes: [
            'Desenvolvedor Front End (Web)',
            'Desenvolvedor Front End (Mobile)',
            'Desenvolvedor Front End (Web e Mobile)',
            'Desenvolvedor Back End',
            'Desenvolvedor Full Stack',
        ],
    }),

    methods: {
        enviar() {
            const formularioEnviado = Object.assign({}, this.desenvolvedor)
            console.log('Formulário enviado:', formularioEnviado)
        },

        resetar() {
            this.desenvolvedor = Object.assign({}, this.valoresPadrão)
        }
    },

    created() {
        this.resetar()
    }
};
</script>

<style scoped>
.btn {
    margin-right: 5px;
}
</style>
