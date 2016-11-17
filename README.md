#【Android自定义View实战】之超简单SearchVIew
效果图

<img src="https://github.com/linglongxin24/SearchVIew/blob/master/screenshorts/effect.jpg?raw=true" width="50%" height="50%"/>

#实现代码

```java
package cn.bluemobi.dylan.searchview;

import android.content.Context;
import android.text.Editable;
import android.text.TextWatcher;
import android.util.AttributeSet;
import android.view.LayoutInflater;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.LinearLayout;

/**
 * Android自定义SearchView
 * Created by yuandl on 2016-11-17.
 */

public class SearchView extends LinearLayout implements TextWatcher, View.OnClickListener {
    /**
     * 输入框
     */
    private EditText et_search;
    /**
     * 输入框后面的那个清除按钮
     */
    private Button bt_clear;


    public SearchView(Context context, AttributeSet attrs) {
        super(context, attrs);
        /**加载布局文件*/
        LayoutInflater.from(context).inflate(R.layout.pub_searchview, this, true);
        /***找出控件*/
        et_search = (EditText) findViewById(R.id.et_search);
        bt_clear = (Button) findViewById(R.id.bt_clear);
        bt_clear.setVisibility(GONE);
        et_search.addTextChangedListener(this);
        bt_clear.setOnClickListener(this);
    }


    @Override
    public void beforeTextChanged(CharSequence charSequence, int i, int i1, int i2) {

    }

    @Override
    public void onTextChanged(CharSequence charSequence, int i, int i1, int i2) {

    }

    /****
     * 对用户输入文字的监听
     *
     * @param editable
     */
    @Override
    public void afterTextChanged(Editable editable) {
        /**获取输入文字**/
        String input = et_search.getText().toString().trim();
        if (input.isEmpty()) {
            bt_clear.setVisibility(GONE);
        } else {
            bt_clear.setVisibility(VISIBLE);
        }
    }

    @Override
    public void onClick(View view) {
        et_search.setText("");
    }
}

```
#[GitHub](https://github.com/linglongxin24/SearchVIew)