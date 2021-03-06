# 日期工具类

```c
package com.java.smallandstrong.pluging.tools.date;

import java.text.ParsePosition;
import java.text.SimpleDateFormat;
import java.util.Date;

/**
 * 
 * @author李栋 日期类型转化工具类
 * https://www.cnblogs.com/sharpest/p/7879377.html
 *
 */
public class VeDateTool {

    /**
     * 返回日期类型
     */

    /**
     * 获取现在时间 返回时间类型 : Date 格式: yyyy-MM-dd HH:mm:ss
     */
    public static Date getNowDate() {
        Date currentTime = new Date();
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String dateString = formatter.format(currentTime);
        ParsePosition pos = new ParsePosition(0);
        Date currentTime_2 = formatter.parse(dateString, pos);
        return currentTime_2;
    }

    /**
     * 入参类型: String 格式: yyyy-MM-dd HH:mm:ss 返回时间类型:Date
     */
    public static Date strToDate(String strDate) {
        // 2019-12-01 24:17:34
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        ParsePosition pos = new ParsePosition(0);
        Date strtodate = formatter.parse(strDate, pos);
        return strtodate;
    }

    /**
     * 入参类型: String  返回时间类型: Date 返回格式 :
     */
  public static Date strToDateShort(String strDate) {
     SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
     ParsePosition pos = new ParsePosition(0);
     Date strtodate = formatter.parse(strDate, pos);
     return strtodate;
  }



  /**
     * 返回String类型
     */

    /**
     * 获取现在时间 返回时间类型:String 格式: yyyy-MM-dd HH:mm:ss
     */
    public static String getStringNowDate() {
        Date currentTime = new Date();
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String dateString = formatter.format(currentTime);
        return dateString;
    }

    /**
     * 获取现在时间 返回时间类型:String 格式: yyyy-MM-dd
     */
    public static String getStringNowDateShort() {
        Date currentTime = new Date();
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
        String dateString = formatter.format(currentTime);
        return dateString;
    }

    /**
     * 获取现在时间 返回时间类型:String 格式: 小时:分;秒 HH:mm:ss
     */
    public static String getNowTimeShort() {
        SimpleDateFormat formatter = new SimpleDateFormat("HH:mm:ss");
        Date currentTime = new Date();
        String dateString = formatter.format(currentTime);
        return dateString;
    }


    /**
     * 入参类型: Date 返回时间类型:String 返回格式:yyyy-MM-dd HH:mm:ss
     */
    public static String dateToStr(java.util.Date dateDate) {
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String dateString = formatter.format(dateDate);
        return dateString;
    }

    /**
     * 入参类型: Date 返回时间类型:String 返回格式 :yyyy-MM-dd
     */
     public static String dateToStrShort(java.util.Date dateDate) {
        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd");
        String dateString = formatter.format(dateDate);
        return dateString;
     }


    public static void main(String[] args) {
        System.out.println(VeDateTool.strToDateShort("2019-01-23 23:23:60"));
    }
}
```

