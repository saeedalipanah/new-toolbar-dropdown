<template>
  <div class="contaiter">
    <div class="toolbar-container">
      <div class="tools" v-for="tool in tools" :key="tool.shortKey">
        <div class="wrapper">
          <input
            type="radio"
            id="input"
            v-model="selectedTool"
            :value="tool.name"
          />
          <span class="material-icons"> {{ tool.icon }} </span>
        </div>
      </div>
    </div>
    <h1> Chosen Tool: {{ selectedTool }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedTool: null,
      tools: [
        {
          name: "Hand-mode",
          icon: "back_hand",
          shortKey: "1",
        },
        {
          name: "Resize-mode",
          icon: "photo_size_select_large",
          shortKey: "2",
        },
        {
          name: "Brush",
          icon: "brush",
          shortKey: "3",
        },
        {
          name: "Magic Pen",
          icon: "auto_fix_high",
          shortKey: "4",
        },
        {
          name: "Pen",
          icon: "edit",
          shortKey: "5",
        },
        {
          name: "Location",
          icon: "location_on",
          shortKey: "6",
        },
        {
          name: "MyLocation",
          icon: "my_location",
          shortKey: "7",
        },
      ],
    };
  },
  mounted(){
    window.addEventListener('keydown', this.ToHandMode);
  },
  methods: {
    ToHandMode(e){
      if(e.code == "Escape")
      this.selectedTool = 'Hand-mode';
    }
  },
};
</script>

<style lang="scss" scoped>
.contaiter {
  height: 100vh;
  width: 100%;
  background: rgba(168, 168, 168, 0.596);
  display: flex;
  justify-content: space-around;
  align-items: center;
  .toolbar-container {
    width: 8%;
    min-width: 110px;
    background: #4a5060;
    border-radius: 2px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 5px;
    // overflow: hidden;
    .tools {
      width: 100%;
      position: relative;
      &::before {
        content: "";
        left: 0;
        top: .5rem;
        width: 8%;
        height: 80%;
        position: absolute;
        background: #00c462;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        display: none;
      }
      &:nth-child(1) {
        border-bottom: 1px solid #7d7d7d;
        padding:1.25rem 0
      }
      &:nth-child(7) {
        margin-bottom: 1.2rem;
      }
      &:hover {
        &::before {
          display: block;
        }
      }
      .wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        input {
          width: 4.4rem;
          height: 4.4rem;
          position: absolute;
          appearance: none;
          z-index: 1000;
          cursor: pointer;
          &:hover + .material-icons {
            color: #00c462;
            animation: shake 0.14s linear 2;
            &::before {
              display: block;
            }
          }
          &:checked + .material-icons {
            transition: all 0.5s ease;
            color: #00c462;
            transform: scale(1.3) rotate(360deg);
            
          }
        }
        .material-icons {
          font-size: 2.5rem;
          margin: 15px 0;
          border-radius: 8px;
          color: #7d7d7d;
        }
      }
    }
  }
  h1{
    color: #555555;
    width: 45%;
    @media only screen and(max-width: 610px){
      font-size: 1.5625rem;
    }
  }
}
@keyframes shake {
  0% {
    transform: translateX(0);
  }
  25% {
    transform: translateX(-5px);
  }
  50% {
    transform: translateX(0);
  }
  75% {
    transform: translateX(5px);
  }
  100% {
    transform: translateX(0px);
  }
}
</style>
