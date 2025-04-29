<template>
  <div class="container">
    <div class="fun-emojis">
      <span>🎉</span><span>🎈</span><span>🎊</span>
    </div>
    <h1>Đơn xin lỗi đóa hồng Bình Tân</h1>
    <h1>Thu Hương</h1>
    <p class="text">
      Xin lỗi bà nhìu, tui thật sự không có ý làm bà khó chịu 😭😭😭.
      Lúc đó tui lên cơn khùm nên có lỡ lời k hay về bà, tưởng rằng nó vô tri nhưng tui giờ hiểu là nó khiến bà cảm thấy không được tôn trọng.
      Tui thành thật xin lỗi và hi vọng bà tha thứ. Tui sẽ xài não trước khi nói để không làm bà khó chịu nữa. 😭😭😭😭
    </p>

    <div class="buttons">
      <button class="btn-forgive" @click="forgive">
        🥺 Pls forgive meeeeee !!!
      </button>

      <button
        ref="noForgiveBtn"
        class="btn-no-forgive"
        @click="moveButton"
        :style="{
          top: noBtnPos.y + 'px',
          left: noBtnPos.x + 'px'
        }"
      >
        Biến giùm cái 😢 !
      </button>
    </div>

    <p class="message" v-if="message">{{ message }}</p>

    <iframe
      class="spotify-embed"
      src="https://open.spotify.com/embed/track/09CtPGIpYB4BrO8qb1RGsF?utm_source=generator"
      width="100%"
      height="352"
      frameborder="0"
      allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
      loading="lazy"
    ></iframe>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "",
      noBtnPos: { x: 0, y: 0 },
    };
  },
  mounted() {
    const cont = this.$el.querySelector(".buttons");
    const btnNo = this.$refs.noForgiveBtn;
    const padding = 20;
    const initX = cont.clientWidth - btnNo.offsetWidth - padding;
    const initY = (cont.clientHeight - btnNo.offsetHeight) / 2;
    this.noBtnPos = { x: initX, y: initY };
  },
  methods: {
    forgive() {
      this.message = "Bà tha thứ cho tui thì cho tui tín hiệu nhé, 2 giây sau nó bưng bà đi liền 😭🙏";
      setTimeout(() => {
        window.location.href = "https://www.instagram.com/htrg.20/";
      }, 2000);
    },
    moveButton() {
      this.message = "Thui tha tui đi má 😭";

      const btnNo = this.$refs.noForgiveBtn;
      btnNo.classList.add("shake");

      setTimeout(() => {
        btnNo.classList.remove("shake");
      }, 500);

      const cont = this.$el.querySelector(".buttons");
      const padding = 10;

      const maxX = cont.clientWidth - btnNo.offsetWidth - padding;
      const maxY = cont.clientHeight - btnNo.offsetHeight - padding;

      let newX, newY;
      do {
        newX = Math.floor(Math.random() * maxX) + padding;
        newY = Math.floor(Math.random() * maxY) + padding;
      } while (
        newX < padding + 120 &&
        newY < cont.clientHeight
      );

      this.noBtnPos = { x: newX, y: newY };
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap');

body {
  margin: 0;
  background: #fefae0;
  font-family: 'Roboto', 'Segoe UI', sans-serif;
}

.container {
  max-width: 700px;
  margin: 40px auto;
  padding: 2rem;
  background-color: #fffdf8;
  border-radius: 20px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  text-align: center;
  animation: fadeIn 1s ease-in-out;
}

h1 {
  color: #e63946;
  font-size: 2.2rem;
  margin: 0.5rem 0;
  font-weight: 700;
  letter-spacing: 1px;
  text-shadow: 1px 1px 2px rgba(0,0,0,0.05);
}

.text {
  color: #333;
  font-size: 1.15rem;
  line-height: 1.75;
  letter-spacing: 0.4px;
  margin-top: 1rem;
  font-weight: 400;
  animation: fadeIn 1.2s ease-in-out;
}

.buttons {
  position: relative;
  height: 80px;
  margin: 30px 0;
}

.btn-forgive {
  position: absolute;
  left: 20px;
  top: 50%;
  transform: translateY(-50%);
  padding: 12px 24px;
  font-weight: 500;
}

.btn-no-forgive {
  position: absolute;
  padding: 12px 24px;
  transition: all 0.4s ease-in-out;
  font-weight: 500;
}

button {
  border: none;
  background-color: #48cae4;
  color: white;
  border-radius: 30px;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.3s ease, transform 0.2s ease;
}
button:hover {
  background-color: #0096c7;
  transform: translateY(-2px);
}

.message {
  margin-top: 20px;
  color: #6c757d;
  font-style: italic;
  font-size: 1.1rem;
  animation: fadeIn 0.6s ease-in-out;
}

.spotify-embed {
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  margin-top: 30px;
}

.fun-emojis {
  margin-bottom: 1rem;
}
.fun-emojis span {
  display: inline-block;
  font-size: 2rem;
  animation: float 3s ease-in-out infinite;
}
.fun-emojis span:nth-child(2) { animation-delay: 0.5s; }
.fun-emojis span:nth-child(3) { animation-delay: 1s; }

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-15px); }
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes shake {
  0% { transform: translate(0, 0); }
  20% { transform: translate(-4px, 0); }
  40% { transform: translate(4px, 0); }
  60% { transform: translate(-4px, 0); }
  80% { transform: translate(4px, 0); }
  100% { transform: translate(0, 0); }
}
.shake {
  animation: shake 0.5s ease;
}

/* Responsive styles */
@media screen and (max-width: 768px) {
  .container {
    margin: 20px;
    padding: 1.2rem;
  }

  h1 {
    font-size: 1.6rem;
  }

  .text {
    font-size: 1rem;
    line-height: 1.6;
  }

  .buttons {
    height: 130px;
  }

  .btn-forgive,
  .btn-no-forgive {
    padding: 10px 16px;
    font-size: 0.9rem;
  }

  .spotify-embed {
    height: 250px;
  }
}

@media screen and (max-width: 480px) {
  .container {
    margin: 15px;
    padding: 1rem;
  }

  h1 {
    font-size: 1.4rem;
  }

  .text {
    font-size: 0.95rem;
  }

  .buttons {
    height: 150px;
  }

  .btn-forgive {
    position: relative;
    left: 0;
    top: 0;
    transform: none;
    margin-bottom: 10px;
  }

  .btn-no-forgive {
    font-size: 0.85rem;
  }

  .spotify-embed {
    height: 220px;
  }
}
</style>
