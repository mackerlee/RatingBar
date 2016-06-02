# RatingBar

android 58 lesson
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
          android:isIndicator="true"/>
  </RelativeLayout>
