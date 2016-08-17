#MULTIBOX

For Box Components you have to output every box in Master.tpl. A MultiBox can contain a number of different components - that can even get created at different levels in the component tree.

This is especially useful for themes where multiple special components can be added in the web and the theme can output them.

###1. Add box(es) in Root_Component

    $ret['generators']['example'] = array(
        'class' => 'Kwf_Component_Generator_MultiBox_Static',
        'component' => 'Example_Component',
        'box' => 'rightBox',
        'inherit' => true
    );
     
     
###2. Output Box in Master.tpl

    <div id="rightBox">
        <?=$this->multiBox('rightBox')?>
    </div>