<template>
  <div class="main posRelative dFlex fJustifyContentCenter fAlignItemsCenter">
    <svg
      id="visual"
      viewBox="0 0 900 600"
      width="100%"
      height="100%"
      preserveAspectRatio="none"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      version="1.1"
    >
      <rect x="0" y="0" width="900" height="600" fill="#001220"></rect>
      <path d="M0 426L21.5 426.2C43 426.3 86 426.7 128.8 419.8C171.7 413 214.3 399 257.2 387.2C300 375.3 343 365.7 385.8 372.7C428.7 379.7 471.3 403.3 514.2 411.3C557 419.3 600 411.7 642.8 404.3C685.7 397 728.3 390 771.2 386.2C814 382.3 857 381.7 878.5 381.3L900 381L900 601L878.5 601C857 601 814 601 771.2 601C728.3 601 685.7 601 642.8 601C600 601 557 601 514.2 601C471.3 601 428.7 601 385.8 601C343 601 300 601 257.2 601C214.3 601 171.7 601 128.8 601C86 601 43 601 21.5 601L0 601Z" fill="#fa7268"></path><path d="M0 400L21.5 410.3C43 420.7 86 441.3 128.8 452C171.7 462.7 214.3 463.3 257.2 463.7C300 464 343 464 385.8 452.5C428.7 441 471.3 418 514.2 408.7C557 399.3 600 403.7 642.8 407.5C685.7 411.3 728.3 414.7 771.2 416C814 417.3 857 416.7 878.5 416.3L900 416L900 601L878.5 601C857 601 814 601 771.2 601C728.3 601 685.7 601 642.8 601C600 601 557 601 514.2 601C471.3 601 428.7 601 385.8 601C343 601 300 601 257.2 601C214.3 601 171.7 601 128.8 601C86 601 43 601 21.5 601L0 601Z" fill="#ef5f67"></path><path d="M0 441L21.5 447.7C43 454.3 86 467.7 128.8 475.8C171.7 484 214.3 487 257.2 482.5C300 478 343 466 385.8 458.2C428.7 450.3 471.3 446.7 514.2 445.3C557 444 600 445 642.8 455.3C685.7 465.7 728.3 485.3 771.2 496C814 506.7 857 508.3 878.5 509.2L900 510L900 601L878.5 601C857 601 814 601 771.2 601C728.3 601 685.7 601 642.8 601C600 601 557 601 514.2 601C471.3 601 428.7 601 385.8 601C343 601 300 601 257.2 601C214.3 601 171.7 601 128.8 601C86 601 43 601 21.5 601L0 601Z" fill="#e34c67"></path><path d="M0 488L21.5 493.5C43 499 86 510 128.8 511.8C171.7 513.7 214.3 506.3 257.2 502.5C300 498.7 343 498.3 385.8 500.2C428.7 502 471.3 506 514.2 507C557 508 600 506 642.8 504.5C685.7 503 728.3 502 771.2 505C814 508 857 515 878.5 518.5L900 522L900 601L878.5 601C857 601 814 601 771.2 601C728.3 601 685.7 601 642.8 601C600 601 557 601 514.2 601C471.3 601 428.7 601 385.8 601C343 601 300 601 257.2 601C214.3 601 171.7 601 128.8 601C86 601 43 601 21.5 601L0 601Z" fill="#d53867"></path><path d="M0 568L21.5 563.8C43 559.7 86 551.3 128.8 550.2C171.7 549 214.3 555 257.2 556.3C300 557.7 343 554.3 385.8 548.2C428.7 542 471.3 533 514.2 534.7C557 536.3 600 548.7 642.8 556.2C685.7 563.7 728.3 566.3 771.2 561.5C814 556.7 857 544.3 878.5 538.2L900 532L900 601L878.5 601C857 601 814 601 771.2 601C728.3 601 685.7 601 642.8 601C600 601 557 601 514.2 601C471.3 601 428.7 601 385.8 601C343 601 300 601 257.2 601C214.3 601 171.7 601 128.8 601C86 601 43 601 21.5 601L0 601Z" fill="#c62368"></path>
    </svg>

    <div class="content posAbsolute dFlex fDirectionColumn fJustifyContentSpaceBetween">
      <h1 class="title taCenter fz40">
        text-to-image
      </h1>

      <div class="print dFlex fJustifyContentCenter fAlignItemsCenter">
        <figure v-if="base64Img.length > 0">
          <img
            :src="base64Img"
            class="print_image"
          >
        </figure>
        <p
          v-else
          class="guide fz12 taCenter"
        >
          아래 설명란에 영어로 텍스트를 작성하고,<br>
          '이미지 생성하기' 버튼을 누르면 여기에 이미지가 생성됩니다.
        </p>
      </div>

      <form class="prompt dFlex mb10">
        <input
          type="text"
          placeholder="영어로 이미지를 설명해주세요."
          required
          v-model="promptText"
          class="prompt_input"
        />
        <input
          type="submit"
          value="이미지 생성하기"
          class="prompt_button pointer fz12 ftw900"
          @click="onClickButton"
        />
      </form>

      <div>
        <p class="desc fz12 taCenter">
          {{ email }}님의 잔여 크래딧은 <span class="ftw900">{{ credits }}</span> 입니다.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      url: process.env.STABILITY_AI_V1_API,
      auth: process.env.STABILITY_AI_AUTH_KEY,
      model: 'stable-diffusion-xl-1024-v1-0',
      email: '',
      credits: 0,
      promptText: '',
      base64Img: ''
    }
  },
  mounted() {
    this.getAccount()
    this.getBalance()
  },
  methods: {
    getAccount() {
      axios({
        url: '/user/account',
        method: 'GET',
        baseURL: this.url,
        headers: {
          Authorization: `Bearer ${this.auth}`
        },
      })
      .then((res) => {
        this.email = res.data.email
      })
      .catch((err) => {
        console.log(err)
      })
    },
    getBalance() {
      axios({
        url: '/user/balance',
        method: 'GET',
        baseURL: this.url,
        headers: {
          Authorization: `Bearer ${this.auth}`
        },
      })
      .then((res) => {
        this.credits = res.data.credits
      })
      .catch((err) => {
        console.log(err)
      })
    },
    postText2Img() {
      const payload = JSON.stringify({
        cfg_scale: 5,
        clip_guidance_preset: 'FAST_BLUE',
        height: 1024,
        width: 1024,
        sampler: 'K_DPM_2_ANCESTRAL',
        samples: 1,
        steps: 40,
        text_prompts: [
          {
            text: this.promptText,
            weight: 1
          }
        ]
      })
      axios({
        url: `/generation/${this.model}/text-to-image`,
        method: 'POST',
        baseURL: this.url,
        headers: {
          'Content-Type': 'application/json',
          Accept: 'application/json',
          Authorization: `Bearer ${this.auth}`
        },
        data: payload
      })
      .then((res) => {
        console.log('base64: ', res.data.artifacts[0].base64)
        this.base64Img = 'data:image/png;base64,' + res.data.artifacts[0].base64
      })
      .catch((err) => {
        console.log('err: ', err)
      })
    },
    onClickButton() {
      this.base64Img = '' // 초기화

      console.log('입력한 prompt: ', this.promptText)

      if (this.promptText.length > 0) {
        this.postText2Img()
      }
    }
  }
}
</script>

<style lang="scss">
@import "~@/assets/scss/app";
</style>