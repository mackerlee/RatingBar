# RatingBar

android 58-59 lesson
1.RatingBar:评分条，基于SeekBar和ProgressBar的扩展，用星型来显示等级评定.使用RatingBar默认大小时，可以触摸/拖动或使用健来设置评.
            也可以用代码设置评分.
    --它有两种样式，小风格用ratingBarStyleSmall，大风格用ratingBarStyleIndicator,其中大的只适合指示，不适合与用户交互；
    --当使用可以支持用户交互的RatingBar时，建议单独放置，而不要将其他控件(widget)放在其左边或右边;
    --只有将它的布局宽设置为wrap_content时，设置的星星的数量(通过函数setNumStars(int)或者在XML的布局文件中定义)才能显示出来，如果
      设置为其他布局如match_parent将无法正确显示星星数量，后果无法预知;
    --事件处理接口：RatingBar.OnRatingBarChangeListener,当星发送改变时触发的动作.

2.RatingBar实例：在res->layout->activity_main.xml中
  <?xml version="1.0" encoding="utf-8"?>
  <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      android:paddingBottom="@dimen/activity_vertical_margin"
      android:paddingLeft="@dimen/activity_horizontal_margin"
      android:paddingRight="@dimen/activity_horizontal_margin"
      android:paddingTop="@dimen/activity_vertical_margin"
      tools:context="com.example.mackerlee.android_58.MainActivity">
  
      <RatingBar
          android:id="@+id/ratingbar01"
          //--宽必须设置为wrap_content
          android:layout_width="wrap_content"
          android:layout_height="wrap_content" 
          //--设置显示星星的最大数量
          android:numStars="6"
          //--设置默认选中几颗星
          android:rating="2"
          //--设置步长，及每次点击增长几颗星
          android:stepSize="0.5"
          //--设置该评星条是否是指示器，如果是true则用户就不能点击，默认不设置是false
          android:isIndicator="false"
          //--设置风格小星星样式
          style="?android:attr/ratingBarStyleSmall"/>
  </RelativeLayout>
  在app->java->包名->MainActivity.java:
            package com.example.mackerlee.android_58;
            
            import android.support.v7.app.AppCompatActivity;
            import android.os.Bundle;
            import android.widget.RatingBar;
            import android.widget.Toast;
            
            public class MainActivity extends AppCompatActivity implements RatingBar.OnRatingBarChangeListener{
            
                private RatingBar rb;
            
                @Override
                protected void onCreate(Bundle savedInstanceState) {
                    super.onCreate(savedInstanceState);
                    setContentView(R.layout.activity_main);
                    rb = (RatingBar)findViewById(R.id.ratingbar01);
                    rb.setOnRatingBarChangeListener(this);
                    //--代码设置星数
                    rb.setRating(3); //代码设置星数为3，如果与xml不一致则仍显示3，这会触发onRatingChanged事件
                }
            
                //--RatingBar响应事件:参数(当前的RatingBar控件,rating是选中的星数是多少,fromUser是表示是否是由用户触发的事件而不是代码设置)
                @Override
                public void onRatingChanged(RatingBar ratingBar, float rating, boolean fromUser) {
                    if(fromUser){
                        //--fromUser为true表示是由用户设置的星数,false表示由代码设置
                        Toast.makeText(this,"您当前选中了"+rating+"颗星",Toast.LENGTH_LONG).show();
                    }
                }
            }

 
