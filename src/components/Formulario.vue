<template>
	<div class="row">
		<div class="col-12">
			<h2 class="text-center"><b>Formulario de contacto</b></h2>
      <hr/>
		</div>
		<div class="col-12 col-sm-12 col-md-6 offset-md-3 col-lg-6 offset-lg-3">
			<form>
				<div class="form-group bmd-form-group">
					<label for="nombre" class="bmd-label-floating">Nombre</label>
					<input
						id="nombre"
						type="text"
						class="form-control"
						v-model="datosPersona.nombre"
					/>
					<span class="bmd-help"></span>
				</div>
				<div class="form-group bmd-form-group">
					<label for="email" class="bmd-label-floating">Email</label>
					<input
						id="email"
						type="email"
						class="form-control"
						v-model="datosPersona.email"
					/>
					<span class="bmd-help"></span>
				</div>
				<div class="form-group bmd-form-group">
					<label for="mensaje" class="bmd-label-floating">Mensaje</label>
					<textarea
						id="mensaje"
						type="text"
						class="form-control"
						v-model="mensaje"
					></textarea>
					<span class="bmd-help"></span>
				</div>
				<div class="row my-4">
					<div class="col-12">
						<small class="text-muted position-absolute"
							>Opciones de email:</small
						>
						<div
							class="d-flex flex-row justify-content-around alignt-items-center"
						>
							<div class="checkbox">
								<label for="enviarMail">
									<input
										type="checkbox"
										id="enviarMail"
										value="enviarMail"
										v-model="opcionesMail"
									/>
									Enviar Email
								</label>
							</div>
							<div class="checkbox">
								<label for="enviarCopia">
									<input
										type="checkbox"
										id="enviarCopia"
										value="enviarCopia"
										v-model="opcionesMail"
									/>
									Enviar Copia
								</label>
							</div>
						</div>
					</div>
				</div>
				<div class="row my-4">
					<div class="col-12">
						<small class="text-muted position-absolute">Genero:</small>
						<div
							class="d-flex flex-row justify-content-around alignt-items-center"
						>
							<div class="radio">
								<label>
									<input
										type="radio"
										name="optGenero"
										id="genMasculino"
										value="masculino"
										v-model="genero"
									/>
									Masculino
								</label>
							</div>
							<div class="radio">
								<label>
									<input
										type="radio"
										name="optGenero"
										id="genFemenino"
										value="femenino"
										v-model="genero"
									/>
									Femenino
								</label>
							</div>
						</div>
					</div>
				</div>
				<div class="row">
					<div class="col-12">
						<div class="form-group">
							<label for="horarios" class="bmd-label-floating">
								Horarios
							</label>
							<select
								name="horarios"
								id="horarios"
								class="form-control"
								v-model="horarioSel"
							>
								<option v-for="horario in horarios" :key="horario">{{
									horario
								}}</option>
							</select>
						</div>
					</div>
				</div>
				<div class="row">
					<div class="col-12">
						<button
							type="submit"
							class="btn btn-raised btn-success btn-block"
							@click.prevent="enviado = true"
						>
							Envia estos datos
						</button>
					</div>
				</div>
			</form>
		</div>
		<div class="col-12" v-show="enviado">
			<hr />
			<div class="card">
				<div class="card-header">
					<h5>
            <b>Datos enviados</b>
          </h5>
				</div>
				<div id="console-body" class="card-body">
					<p class="card-text"><b>Nombre:</b> {{ datosPersona.nombre }}</p>
					<p class="card-text"><b>Email:</b> {{ datosPersona.email }}</p>
					<p class="card-text" style="white-space: pre">
						<b>Mensaje:</b> {{ mensaje }}
					</p>
					<p class="card-text" style="white-space: pre">
						<b>Opciones para Email:</b>
						<br />
						<transition-group name="component-fade" mode="out-in" tag="ul">
							<li v-for="opcion in opcionesMail" :key="opcion">{{ opcion }}</li>
						</transition-group>
					</p>
					<p class="card-text"><b>Genero:</b> {{ genero }}</p>
					<p class="card-text"><b>Horario:</b> {{ horarioSel }}</p>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	export default {
		data() {
			return {
				datosPersona: {
					nombre: '',
					email: '',
				},
				mensaje: '',
				opcionesMail: [],
				genero: 'masculino',
				horarios: ['mañana', 'tarde', 'noche'],
				horarioSel: 'mañana',
				enviado: false,
			}
		},
	}
</script>
<style scoped>
	label.bmd-label-floating::after {
		content: ':';
	}
	#console-body {
		height: 200px;
		overflow-y: scroll;
	}
	.component-fade-enter-active,
	.component-fade-leave-active {
		transition: opacity 0.3s ease;
	}
	.component-fade-enter, .component-fade-leave-to
/* .component-fade-leave-active below version 2.1.8 */ {
		opacity: 0;
	}
</style>
