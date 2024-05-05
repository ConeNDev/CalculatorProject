<template>
<!DOCTYPE html>
<html>
  
<!-- create table -->
  
<body>
  <h1>Calculator Nemanja</h1>
    <table id="calcu">
        <tr>
            <td colspan="3"><input v-model="broj" type="text" id="result"></td>
            <!-- clr() function will call clr to clear all value -->
            <td><input type="button" value="c" @click="clear()"  /> </td>
        </tr>
        <tr>
            <!-- create button and assign value to each button -->
            <!-- dis("1") will call function dis to display value -->
            <td><input  type="button" value="1" @click=" writeIt(1)"> </td>
            <td><input type="button" value="2"  @click=" writeIt(2)"> </td>
            <td><input type="button" value="3" @click=" writeIt(3)"> </td>
            <td><input type="button" value="/" @click="divide()" > </td>
        </tr>
        <tr>
            <td><input type="button" value="4" @click=" writeIt(4)"> </td>
            <td><input type="button" value="5" @click=" writeIt(5)"> </td>
            <td><input type="button" value="6" @click=" writeIt(6)"> </td>
            <td><input type="button" value="*" @click="multiply()" > </td>
        </tr>
        <tr>
            <td><input type="button" value="7" @click=" writeIt(7)"> </td>
            <td><input type="button" value="8" @click=" writeIt(8)"> </td>
            <td><input type="button" value="9" @click=" writeIt(9)"> </td>
            <td><input type="button" value="-" @click="substract()" > </td>
        </tr>
        <tr>
            <td><input type="button" value="0" @click=" writeIt(0)" > </td>
            <td><input type="button" value="." @click="writeIt('.')"> </td>
            <!-- solve function call function solve to evaluate value -->
            <td><input type="button" value="=" @click="equals()"> </td>
  
            <td><input type="button" value="+" @click="sum()"> </td>
        </tr>
    </table>
  
</body>
  
</html>   
</template>

<script>
import { throwStatement } from '@babel/types'

export default{
  data(){
    return{
      broj:'',
      previous:0,
      numAdd:0,
      numDiv:0,
      numSubstr:0,
      numMul:0
    }
  },
  methods:{
    writeIt(br){
      
      if(this.broj[0]!='0'){
          this.broj+=br
      }
      else{
        this.broj=br
      }
    },
    equals(){
      if(this.numAdd>0){
        
        this.broj=Number(this.broj)+Number(this.previous)
      }
      if(this.numDiv>0){
        
        this.broj=Number(this.previous)/Number(this.broj)
      }
      if(this.numMul>0){
        
        this.broj=Number(this.broj)*Number(this.previous)
      }
      if(this.numSubstr>0){
        
        this.broj=Number(this.previous)-Number(this.broj)
      }
      
      this.previous=0
      this.numDiv=0
      this.numSubstr=0
      this.numMul=0

    },
    clear(){
      this.broj=''
      this.previous=0,
      this.numAdd=0,
      this.numDiv=0,
      this.numSubstr=0,
      this.numMul=0
    },
    divide(){
      this.numDiv++
      if(this.numDiv==1){
          this.previous=Number(this.broj)
      }
      else{
          this.previous=Number(this.previous)/Number(this.broj)
      }
      
      this.broj=''
      
      
    },
    sum(){
      
      this.previous=Number(this.previous)+Number(this.broj)
      this.broj=''
      this.numAdd++
      
    },
    
    substract(){
      this.numSubstr++
      if(this.numSubstr==1){
          this.previous=Number(this.broj)-Number(this.previous)
      }
      else{
          this.previous=Number(this.previous)-Number(this.broj)
      }
      
      this.broj=''
      
      
    },
    multiply(){
      this.numMul++
      if(this.numMul==1){
        this.previous=Number(this.broj)
      }
      else{
        this.previous=Number(this.broj)*Number(this.previous)
      }
      this.broj=''

    },

  }
}
</script>

<style>
        table {
            border: 1px solid black;
            margin-left: auto;
            margin-right: auto;
        }
  
        input[type="button"] {
            width: 100%;
            padding: 20px 40px;
            background-color: green;
            color: white;
            font-size: 24px;
            font-weight: bold;
            border: none;
            border-radius: 5px;
        }
  
        input[type="text"] {
            padding: 20px 30px;
            font-size: 24px;
            font-weight: bold;
            border: none;
            border-radius: 5px;
            border: 2px solid black;
        }
</style>
