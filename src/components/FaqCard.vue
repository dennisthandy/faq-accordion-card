<template>
	<div class="container">
		<div class="card">
			<img
				src="../assets/images/illustration-woman-online-mobile.svg"
				alt="Woman Ilustration"
				class="card__img card__img__mobile__ilustration"
			/>

			<img
				src="../assets/images/bg-pattern-mobile.svg"
				alt="Shadow Ilustration"
				class="card__img card__img__mobile__shadow"
			/>

			<img
				src="../assets/images/illustration-woman-online-desktop.svg"
				alt="Woman Ilustration"
				class="card__img card__img__desktop__ilustration"
			/>

			<img
				src="../assets/images/bg-pattern-desktop.svg"
				alt="Shadow Ilustration"
				class="card__img card__img__desktop__shadow"
			/>

			<div class="card__content">
				<h1 class="card__title">FAQ</h1>
				<ul class="card__faqs-list">
					<li
						class="card__faqs-item"
						v-for="faq in faqs"
						:key="faq.id"
						@click="handleOpenFaq(faq.id)"
					>
						<p
							:class="[
								selectedFaq(faq.id) ? 'selected' : '',
								'card__faqs-item__question',
							]"
						>
							{{ faq.question }}
							<svg
								width="10"
								height="7"
								xmlns="http://www.w3.org/2000/svg"
								:class="[
									selectedFaq(faq.id) ? 'up' : '',
									'card__faqs-item__arrow',
								]"
							>
								<path
									d="M1 .799l4 4 4-4"
									stroke="#F47B56"
									stroke-width="2"
									fill="none"
									fill-rule="evenodd"
								/>
							</svg>
						</p>
						<p
							:class="[
								selectedFaq(faq.id) ? 'open' : '',
								'card__faqs-item__answer',
							]"
						>
							{{ faq.answer }}
						</p>
					</li>
				</ul>
			</div>
		</div>
		<img
			src="../assets/images/illustration-box-desktop.svg"
			alt="Woman Ilustration"
			class="card__img card__img__box__ilustration"
		/>
	</div>
</template>

<script>
	export default {
		data: function () {
			return {
				faqs: [
					{
						id: 0,
						question: 'How many team members can I invite?',
						answer: 'This is the answer.',
					},
					{
						id: 1,
						question: 'What is the maximum file upload size?',
						answer:
							'No more than 2GB. All files in your account must fit your allotted storage space.',
					},
					{
						id: 2,
						question: 'How do I reset my password?',
						answer: 'This is the answer.',
					},
					{
						id: 3,
						question: 'Can I cancel my subscription?',
						answer: 'This is the answer.',
					},
					{
						id: 4,
						question: 'Do you provide additional support?',
						answer: 'This is the answer.',
					},
				],
				openFaqId: 1,
				showAnswer: true,
			};
		},
		methods: {
			handleOpenFaq(faqId) {
				this.openFaqId = faqId;
				this.showAnswer = true;
			},
			selectedFaq(faqId) {
				return faqId == this.openFaqId && this.showAnswer;
			},
		},
	};
</script>

<style lang="scss" scoped>
	.container {
		position: relative;
	}

	.card {
		width: 17rem;
		height: 20rem;
		background: white;
		margin: 10rem 0 5rem 0;
		border-radius: 1.5rem;
		position: relative;
		padding: 8rem 1.25rem 3rem 1.25rem;
		box-shadow: 0 20px 30px rgba(0, 0, 0, 0.3);

		@media screen and (min-width: $desktop) {
			margin: auto;
			width: 55rem;
			padding: 5rem 0;
			overflow: hidden;
		}

		&__img {
			position: absolute;

			&__mobile__ilustration {
				top: -33.5%;
				left: 50%;

				transform: translate(-55%, 33.5%);
				@media screen and (min-width: $desktop) {
					display: none;
				}
			}

			&__mobile__shadow {
				left: 12%;
				top: -0.5%;

				@media screen and (min-width: $desktop) {
					display: none;
				}
			}

			&__desktop__ilustration {
				display: none;

				@media screen and (min-width: $desktop) {
					display: block;
					left: -9%;
					top: 12%;
					z-index: 1;
				}
			}

			&__box__ilustration {
				display: none;

				@media screen and (min-width: $desktop) {
					display: block;
					left: -10%;
					top: 40%;
					z-index: 9;
				}
			}

			&__desktop__shadow {
				display: none;

				@media screen and (min-width: $desktop) {
					display: block;
					top: -62%;
					left: -61%;
					z-index: 0;
					transform: scale(0.9);
				}
			}
		}

		&__content {
			@media screen and (min-width: $desktop) {
				position: absolute;
				right: 5rem;
				width: 20rem;
			}
		}

		&__title {
			text-align: center;
			color: $text-primary-very-dark-desaturated-blue;

			@media screen and (min-width: $desktop) {
				text-align: left;
			}
		}

		&__faqs-list {
			margin-top: 2rem;
			display: grid;
			gap: 1rem;
		}

		&__faqs-item {
			font-size: $font-body;
			padding: 0 0 1rem 0;
			border-bottom: 1px solid $dividers-light-grayish-blue;
			cursor: pointer;

			@media screen and (min-width: $desktop) {
				font-size: 14px;
			}

			&__question {
				display: flex;
				justify-content: space-between;
				align-items: center;
				color: $text-neutral-very-dark-grayish-blue;

				&.selected {
					color: $text-primary-very-dark-desaturated-blue;
					font-weight: bold;
				}
			}

			&__answer {
				display: none;

				&.open {
					display: block;
					margin-top: 1rem;
					color: $text-neutral-dark-grayish-blue;
					padding-right: 0.25rem;
					line-height: 1.15rem;
					font-size: $font-body;
				}
			}

			&__arrow {
				&.up {
					transform: rotate(180deg);
				}
			}
		}
	}
</style>
