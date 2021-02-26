<template>
  <div id="app">
    <div class="body">
      <Form :model="formItem" :label-width="80" class="myForm">
        <h1>Some info of you</h1>
        <FormItem label="Nickname">
          <Input v-model="formItem.input" placeholder="Enter something..." class="inputText"/>
        </FormItem>
        <FormItem label="Country">
          <Select v-model="formItem.select" class="inputSelect" placeholder="select">
            <Option value="beijing">Ukraine</Option>
            <Option value="shanghai">USA</Option>
            <Option value="shenzhen">Russia</Option>
          </Select>
        </FormItem>
        <FormItem label="Date" class="Date">
          <Row>
            <Col span="11">
              <DatePicker type="date" placeholder="Select date" v-model="formItem.date" class="inputDate"></DatePicker>
            </Col>
            <Col span="2" style="text-align: center"><span>-</span></Col>
            <Col span="11">
              <TimePicker type="time" placeholder="Select time" v-model="formItem.time" class="inputDate"></TimePicker>
            </Col>
          </Row>
        </FormItem>
        <FormItem label="Sex">
          <RadioGroup v-model="formItem.radio" class="radioButtons">
            <Radio label="male" class="maleRadio"><span>Male</span></Radio>
            <Radio label="female" class="femaleRadio"><span>Female</span></Radio>
          </RadioGroup>
        </FormItem>
        <FormItem label="Hobby">
          <CheckboxGroup v-model="formItem.checkbox" class="checkboxButtons">
            <Checkbox label="Eat" class="checkboxButton"></Checkbox>
            <Checkbox label="Sleep" class="checkboxButton"></Checkbox>
            <Checkbox label="Run" class="checkboxButton"></Checkbox>
            <Checkbox label="Movie" class="checkboxButton"></Checkbox>
          </CheckboxGroup>
        </FormItem>
        <FormItem label="Married">
          <i-switch v-model="formItem.switch" size="large" class="switchButton">
            <span slot="open" class="switch">Yes</span>
            <span slot="close">No</span>
          </i-switch>
        </FormItem>
        <FormItem label="Age">
          <Slider v-model="formItem.slider" range class="rangeSlider"></Slider>
        </FormItem>
        <FormItem label="Whishes">
          <Input class="textArea" v-model="formItem.textarea" type="textarea" :autosize="{minRows: 2,maxRows: 5}" placeholder="Enter your whishes..."></Input>
        </FormItem>
        <FormItem class="Buttons">
          <Button  class="buttonSubmit">Send</Button>
          <Button style="margin-left: 8px"  class="buttonCancel">Cancel</Button>
        </FormItem>
      </Form>
      <div>{{url}}</div>
      <div>{{title}}</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data: function () {
      return {
        formItem: {
          input: '',
          select: '',
          radio: 'male',
          checkbox: [],
          switch: true,
          date: '',
          time: '',
          slider: [0, 50],
          textarea: ''
        },
        url: process.env.VUE_APP_URL,
        title: process.env.VUE_APP_TITLE
      }
    }
  }
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
/*vars==========================*/
@colorYellow: #e4df1b;
/*Mixins=====================================*/
.inputStyle() {
  background-color: transparent;
  border: 2px solid @colorYellow;
  border-radius: 15px;
  height: 35px;
}
.floatLeft() {
  float: left;
  margin-left: 5px;
}
.btnTemplate() {
  width: 175px;
  height: 40px;
  border-radius: 15px;
  span {
    font-size: 16px;
    color: #ffffff;
    font-weight: 700;
  }
}
/*======================================*/

/*Form styles */
.myForm {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  max-width: 550px;
  margin: 40px auto;
  padding: 10px 20px 20px;
  border-radius: 30px;
  background-color: #182635;
  box-shadow: 0 0 30px 20px rgba(0, 0, 0, 0.2);

  h1 {
    color: #ffffff;
    font-weight: 700;
    font-size: 40px;
    padding-bottom: 25px;
  }

  .ivu-form-item {
    width: 100%;

    .ivu-form-item-label {
      color: @colorYellow;
      float: left;
      font-weight: 700;
      font-size: 16px;
      text-align: center;
    }

  }

}
.inputText {

  .ivu-input {

    &[type="text"] {
      color: #ffffff;
    }
    .inputStyle();
    &::placeholder {
      color: #ffffff;
    }
  }
}
.inputSelect {

  &.ivu-select-single {
    .ivu-select-selection {

      .inputStyle();
      height: 35px !important;
      .ivu-select-selected-value {
        color: #ffffff;
      }
      .ivu-select-placeholder {
        color: #ffffff;
        float: left;
      }
      .ivu-select-arrow {
        color: @colorYellow;
      }
    }
  }

}

.Date {

  .ivu-col-span-2 {
    color: @colorYellow;
    font-weight: 700;
    font-size: 25px;
  }
  .inputDate {

    .ivu-input {
      .inputStyle();

      &::placeholder {
        color: #ffffff;
      }
      &[type="text"] {
        color: #ffffff;
      }

    }
    .ivu-input-suffix i {
      color: @colorYellow;
    }
    .ivu-date-picker-cells-focused em {
      box-shadow: 0 0 0 1px @colorYellow inset;
    }
    .ivu-date-picker-cells-cell-today em::after {
      background: #000000;
    }
  }
}
.radioButtons {
  .floatLeft();
  margin-left: 0;

  &.ivu-radio-group {
    .inputStyle();
    padding: 0 25px;
  }
  .maleRadio {
    span {
      color: #ffffff;
    }
    .ivu-radio-inner {
      background-color: transparent;
      border: 2px solid #ffffff;

      &::after {
        background-color: #d3cf1d;
      }
    }

  }
  .femaleRadio {
    span {
      color: #ffffff;
    }
    .ivu-radio-inner {
      background-color: transparent;
      border: 2px solid #ffffff;

      &::after {
        background-color: #d3cf1d;
      }
    }
  }
}
.checkboxButtons {
  .floatLeft();

  &.ivu-checkbox-group {
    .inputStyle();
    padding: 0 25px;
  }
  .checkboxButton {
    color: #ffffff;
    .ivu-checkbox-checked {
      .ivu-checkbox-inner {
        background-color: #d3cf1d;
        border: 2px solid #000000;

        &::after {
          border: 2px solid #000;
          border-top: 0;
          border-left: 0;
        }
      }
    }
    .ivu-checkbox-inner {
      background-color: transparent;
      border: 2px solid #ffffff;
    }
  }
}
.switchButton {
  .floatLeft();
  margin-top: 5px;

  &.ivu-switch {
    border-color: red;
    background-color: red;
  }
  &.ivu-switch-checked {
    border-color: #00a158;
    background-color: #00a158;
  }

}
.Buttons {
  .ivu-form-item-content {
    margin-left: 0 !important;
  }
  .buttonSubmit {
    .btnTemplate();
    border: 2px solid @colorYellow;
    background-color: @colorYellow;

    span {
      color: #000000;
    }

    &:hover {
      border: 2px solid #00a158;
      background-color: #00a158;

      span {
        color: #ffffff;
      }
    }

  }
  .buttonCancel {
    .btnTemplate();
      border: 2px dashed @colorYellow;
      background-color: transparent;
      &:hover {
        border: 2px solid red;
        background-color: red;

        span {
          color: #ffffff;
        }
      }
  }
}
.rangeSlider {
  .ivu-slider-wrap {
    background-color: #000000;
    .ivu-slider-button {
      border: 2px solid #000000;
      background-color: #d3cf1d;
    }
    .ivu-slider-bar {
      background: #d3cf1d;
    }
  }
}
.textArea {

  .ivu-input {
    background-color: transparent;
    resize: none;
    border: 2px dashed #d3cf1d;

    &[type="text"] {
      color: #ffffff;
    }

    &:hover {
      border: 2px dashed #d3cf1d;
    }
    &:focus {
      border: 2px dashed #d3cf1d;
    }

    &::placeholder {
      color: #ffffff;
    }
  }
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
