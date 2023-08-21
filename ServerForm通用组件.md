# ServerForm通用组件
ServerForm的UI修改不能简单的使用修改插入变量
为了实现一个多修改不冲突的ServerForm
我的建议使用如下组件覆盖
```json
{
  "namespace": "server_form",
  "long_form": {
    "type": "panel",
    "controls": [
      {
        "form@common_dialogs.main_panel_no_buttons": {
          "$title_panel": "common_dialogs.standard_title_label",
          "$title_size": [ "100% - 14px", 10 ],
          "size": [225, 200],
          "$text_name": "#title_text",
          "$title_text_binding_type": "none",
          "$child_control": "server_form.long_form_panel",
          "bindings": [
            {
              "binding_name": "#title_text"
            },
            {
              "binding_type": "view",
              "source_property_name": "(((#title_text - '你的UI通用标题') = #title_text) or (not ((#title_text - '关键词检测') = #title_text)))",
              "target_property_name": "#visible"
            }
          ]
        }
      }
    ]
  }
}
```
在此后使用修改插入controls即可
