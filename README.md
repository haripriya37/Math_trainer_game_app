# Math_trainer_game_app
#This is a simple math brain trainer implemented in Java and build using Android studio.
#The below code is to be written in MainActivity.java file, run this to play simple math additions game
package com.rharipriya.math_trainer;

import android.os.CountDownTimer;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.text.Layout;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.GridLayout;
import android.widget.TextView;

import java.util.Random;

public class MainActivity extends AppCompatActivity {
    TextView timerTextview;
    TextView question;
    TextView marks;
    TextView result;
    Button op1;
    Button op2;
    Button op3;
    Button op4;
    boolean timerdone=false;
    int total;
    int crct;


    Random rand=new Random();
    int x=rand.nextInt(30);
    int y=rand.nextInt(30);
    int answer=x+y;
    int ansbutton=rand.nextInt(4);

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        timerTextview=(TextView)findViewById(R.id.timerTextview);
        question =(TextView)findViewById(R.id.question);
        marks =(TextView)findViewById(R.id.marks);
        result=(TextView)findViewById(R.id.result);
        op1=(Button)findViewById(R.id.op1);
        op2=(Button)findViewById(R.id.op2);
        op3=(Button)findViewById(R.id.op3);
        op4=(Button)findViewById(R.id.op4);

        question.setText(Integer.toString(x)+"+"+Integer.toString(y));

        timerTextview.setVisibility(View.GONE);
        question.setVisibility(View.GONE);
        marks.setVisibility(View.GONE);
        result.setVisibility(View.GONE);
        op1.setVisibility(View.GONE);
        op2.setVisibility(View.GONE);
        op3.setVisibility(View.GONE);
        op4.setVisibility(View.GONE);

        if(ansbutton==0||ansbutton==1) {
            op1.setText(Integer.toString(answer));
            op2.setText(Integer.toString(rand.nextInt(30)));
            op3.setText(Integer.toString(rand.nextInt(30)));
            op4.setText(Integer.toString(rand.nextInt(30)));
        }
        else if(ansbutton==2) {
            op1.setText(Integer.toString(rand.nextInt(30)));
            op2.setText(Integer.toString(answer));
            op3.setText(Integer.toString(rand.nextInt(30)));
            op4.setText(Integer.toString(rand.nextInt(30)));
        }
        else if(ansbutton==3) {
            op1.setText(Integer.toString(rand.nextInt(30)));
            op2.setText(Integer.toString(rand.nextInt(30)));
            op3.setText(Integer.toString(answer));
            op4.setText(Integer.toString(rand.nextInt(30)));
        }
        else if(ansbutton==4) {
            op1.setText(Integer.toString(rand.nextInt(30)));
            op2.setText(Integer.toString(rand.nextInt(30)));
            op3.setText(Integer.toString(answer));
            op4.setText(Integer.toString(answer));
        }


    }
    public void goFunction(View view){
        Button goButton=(Button)findViewById(R.id.goButton);
        goButton.setVisibility(View.GONE);
        timerTextview=(TextView)findViewById(R.id.timerTextview);
        question =(TextView)findViewById(R.id.question);
        marks =(TextView)findViewById(R.id.marks);
        result=(TextView)findViewById(R.id.result);
        op1=(Button)findViewById(R.id.op1);
        op2=(Button)findViewById(R.id.op2);
        op3=(Button)findViewById(R.id.op3);
        op4=(Button)findViewById(R.id.op4);


        timerTextview.setVisibility(View.VISIBLE);
        question.setVisibility(View.VISIBLE);
        marks.setVisibility(View.VISIBLE);
        result.setVisibility(View.VISIBLE);
        op1.setVisibility(View.VISIBLE);
        op2.setVisibility(View.VISIBLE);
        op3.setVisibility(View.VISIBLE);
        op4.setVisibility(View.VISIBLE);


        new CountDownTimer(10000,1000){
            public void onTick(long millisecondsuntildone)
            {
                //counting down every second
                //Log.i("seconds left:",String.valueOf(millisecondsuntildone/1000));
                /*if((millisecondsuntildone/1000)==3)
                    generateq();*/
                if((millisecondsuntildone/1000)>9)
                timerTextview.setText("0:"+String.valueOf(millisecondsuntildone/1000));
                else
                    timerTextview.setText("0:0"+String.valueOf(millisecondsuntildone/1000));

            }
            public void onFinish()
            {
                //after 10secs
                Log.i("hiis","huud");
                timerdone=true;
            }
        }.start();

    }
    public void eval1(View view){
        if(!timerdone){
            op1=(Button)findViewById(R.id.op1);
            String userans= (String) op1.getText();
            int ua=Integer.parseInt(userans);
            result=(TextView)findViewById(R.id.result);
            if(ua==answer){
                result.setText("You are right!");
                crct++;
            }
            else
                result.setText("Try again!");
            total++;
            marks.setText(Integer.toString(crct)+"/"+Integer.toString(total));
            x=rand.nextInt(30);
            y=rand.nextInt(30);
            answer=x+y;

            question =(TextView)findViewById(R.id.question);
            marks =(TextView)findViewById(R.id.marks);
            op1=(Button)findViewById(R.id.op1);
            op2=(Button)findViewById(R.id.op2);
            op3=(Button)findViewById(R.id.op3);
            op4=(Button)findViewById(R.id.op4);

            question.setText(Integer.toString(x)+"+"+Integer.toString(y));

            if(ansbutton==0||ansbutton==1) {
                op1.setText(Integer.toString(answer));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==2) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(answer));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==3) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==4) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(answer));
            }
        }
        else {result.setText("Times up!");
            marks.setText(Integer.toString(crct)+"/"+Integer.toString(total));}
    }
    public void eval2(View view){
        if(!timerdone){
            op2=(Button)findViewById(R.id.op2);
            String userans= (String) op2.getText();
            int ua=Integer.parseInt(userans);
            result=(TextView)findViewById(R.id.result);
            if(ua==answer){
                result.setText("You are right!");
                crct++;
            }
            else
                result.setText("Try again!");
            total++;
            marks.setText(Integer.toString(crct)+"/"+Integer.toString(total));
            x=rand.nextInt(30);
            y=rand.nextInt(30);
            answer=x+y;

            question =(TextView)findViewById(R.id.question);
            marks =(TextView)findViewById(R.id.marks);
            op1=(Button)findViewById(R.id.op1);
            op2=(Button)findViewById(R.id.op2);
            op3=(Button)findViewById(R.id.op3);
            op4=(Button)findViewById(R.id.op4);

            question.setText(Integer.toString(x)+"+"+Integer.toString(y));

            if(ansbutton==0||ansbutton==1) {
                op1.setText(Integer.toString(answer));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==2) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(answer));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==3) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==4) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(answer));
            }
        }
        else {
            result.setText("Times up!");
            marks.setText(Integer.toString(crct) + "/" + Integer.toString(total));
        }
    }
    public void eval3(View view){
        if(!timerdone){
            op3=(Button)findViewById(R.id.op3);
            String userans= (String) op3.getText();
            int ua=Integer.parseInt(userans);
            result=(TextView)findViewById(R.id.result);
            if(ua==answer){
                crct++;
                result.setText("You are right!");
            }
            else
                result.setText("Try again!");
            total++;
            marks.setText(Integer.toString(crct)+"/"+Integer.toString(total));
            x=rand.nextInt(30);
            y=rand.nextInt(30);
            answer=x+y;

            question =(TextView)findViewById(R.id.question);
            marks =(TextView)findViewById(R.id.marks);
            result=(TextView)findViewById(R.id.result);
            op1=(Button)findViewById(R.id.op1);
            op2=(Button)findViewById(R.id.op2);
            op3=(Button)findViewById(R.id.op3);
            op4=(Button)findViewById(R.id.op4);

            question.setText(Integer.toString(x)+"+"+Integer.toString(y));

            if(ansbutton==0||ansbutton==1) {
                op1.setText(Integer.toString(answer));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==2) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(answer));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==3) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==4) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(answer));
            }
        }
        else {
            result.setText("Times up!");
            marks.setText(Integer.toString(crct) + "/" + Integer.toString(total));
        }

    }
    public void eval4(View view){
        if(!timerdone){
            op4=(Button)findViewById(R.id.op4);
            String userans= (String) op4.getText();
            int ua=Integer.parseInt(userans);
            result=(TextView)findViewById(R.id.result);
            if(ua==answer){
                crct++;
                result.setText("You are right!");
            }
            else
                result.setText("Try again!");
            total++;
            marks.setText(Integer.toString(crct)+"/"+Integer.toString(total));
            x=rand.nextInt(30);
            y=rand.nextInt(30);
            answer=x+y;

            question =(TextView)findViewById(R.id.question);
            marks =(TextView)findViewById(R.id.marks);
            result=(TextView)findViewById(R.id.result);
            op1=(Button)findViewById(R.id.op1);
            op2=(Button)findViewById(R.id.op2);
            op3=(Button)findViewById(R.id.op3);
            op4=(Button)findViewById(R.id.op4);

            question.setText(Integer.toString(x)+"+"+Integer.toString(y));

            if(ansbutton==0||ansbutton==1) {
                op1.setText(Integer.toString(answer));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==2) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(answer));
                op3.setText(Integer.toString(rand.nextInt(30)));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==3) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(rand.nextInt(30)));
            }
            else if(ansbutton==4) {
                op1.setText(Integer.toString(rand.nextInt(30)));
                op2.setText(Integer.toString(rand.nextInt(30)));
                op3.setText(Integer.toString(answer));
                op4.setText(Integer.toString(answer));
            }
        }
        else {
            result.setText("Times up!");
            marks.setText(Integer.toString(crct) + "/" + Integer.toString(total));
        }
    }


    //public void generateq(){
       // Random rand=new Random();
       // int x=rand.nextInt(30);
       // int y=rand.nextInt(30);

   // }
}
