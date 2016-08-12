#BACKEND MENU

The top menu is shown by default on all backend pages. To add menu items simply add them to the [Acl](../acl.md). But you can further modify the menu and add any other custom functionality by implementing your own menu class.

This example adds a second combobox similar to the change user combobox:

    var Menu = Ext.extend(Kwf.Menu.Index,
    {
        controllerUrl: '/admin/misc/menu', //optional, to add additional data to response
        loadMenu: function(response, options, result)
        {
            Menu.superclass.loadMenu.apply(this, arguments);
            if (Kwf.userRole == 'admin') {
                var changeXxx = new Kwf.Form.ComboBox({
                    store: {
                        url: '/admin/misc/change-xxx/json-data'
                    },
                    mode: 'remote',
                    triggerAction: 'all',
                    typeAhead: true,
                    width: 60,
                    listWidth: 60,
                    selectOnFocus: true,
                    minChars: 2,
                    emptyText: trl('Xxx'),
                    tpl: new Ext.XTemplate(
                            '<tpl for=".">',
                            '<div class="x-combo-list-item">',
                                '{xxx}',
                            '</div>',
                            '</tpl>')
                });
                changeXxx.on('render', function(combo) {
                    if (result.changeXxx) { //from custom menu action
                        combo.setRawValue(result.changeXxx);
                    }
                }, this, {delay: 10});
                changeXxx.on('select', function(combo, record, index) {
                    Ext.Ajax.request({
                        url: '/admin/misc/change-xxx/json-change-xxx',
                        params: { xxx: record.id },
                        success: function() {
                            location.href = location.href;
                        },
                        scope: this
                    });
                }, this);
                this.insert(this.items.indexOfKey('currentUser')-1, changeXxx);
            }
        }
    });
    Ext.reg('kwf.menu', Menu);
     