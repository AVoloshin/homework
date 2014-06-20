homework
========
function veloStrPad ($string,$length=0,$padString=' ',$padType=STR_PAD_RIGHT){
    $numStr=0;$numPad=0;
    while($string[$numStr]!=NULL){  //считаем длину входной строки
        $numStr++;
    }
    var_dump($numStr);
    while($padString[$numPad]!=NULL){  //считаем длину входной строки
        $numPad++;
    }
    var_dump($numPad);
    $dif=($length-$numStr); //считаем кол-во символов, которые нужно дополнить
    var_dump($dif);
    $tmp='';$tmp1='';$tmp2='';
    if(isset($padType)){
        if($dif<$numPad){
            for($i=0;$i<$dif;$i++){   //собираем символы для заполнения справа
                $tmp1.=$padString[$i];
            }
            $tmp.=$tmp1;
        }
        elseif(!($dif%$numPad)){
            for($i=0;$i<$dif/$numPad;$i++){
                $tmp.=$padString;
            }
        }
        elseif(($dif%$numPad) && ($dif/$numPad)>0){
            for($i=0;$i<($dif/$numPad);$i++){
                $tmp=$padString;
            }
            $x=(int)($dif/$numPad);
            for($j=0;$j<($dif-$x*$numPad);$j++){
              $tmp2.=$padString[$j];
            }
            $tmp=$tmp.$tmp2;
        }
    }
    var_dump($tmp);
    if ($padType===STR_PAD_RIGHT){
        $string.=$tmp;
    }

    elseif($padType===STR_PAD_LEFT){
        $string=$tmp.$string;
    }
    elseif($padType===STR_PAD_BOTH){
        $ztmp='';$ztmp1='';$ztmp2='';$ztmp3='';
        $z=($dif/2);
        var_dump($z);

        if($z<$numPad){
            for($i=0;$i<$z;$i++){   //собираем символы для заполнения справа
                $ztmp1.=$padString[$i];
            }
            $ztmp.=$ztmp1;
        }
        elseif(!($z%$numPad)){
            for($i=0;$i<$z/$numPad;$i++){
                $ztmp.=$padString;
            }

        }
        elseif(($z%$numPad) && ($z/$numPad)>0){
            for($i=0;$i<($dif/$numPad);$i++){
                $ztmp=$padString;
            }
            $x=(int)($z/$numPad);
            for($j=0;$j<($z-$x*$numPad);$j++){
                $ztmp2.=$padString[$j];
            }
            $ztmp=$ztmp.$ztmp2;
        }

        $xtmp='';$xtmp1='';$xtmp2='';
            if($z<$numPad){
                for($i=0;$i<($z-1);$i++){   //собираем символы для заполнения справа
                    $xtmp1.=$padString[$i];
                }
                $ztmp3.=$xtmp1;
            }
            elseif(!($z%$numPad)){
                for($i=0;$i<$z/$numPad;$i++){
                    $ztmp3.=$padString;
                }

            }
            elseif(($z%$numPad) && ($z/$numPad)>0){
                for($i=0;$i<($dif/$numPad);$i++){
                    $xtmp=$padString;
                }
                $x=(int)($z/$numPad);
                for($j=0;$j<(($z-$x*$numPad)-1);$j++){
                    $xtmp2.=$padString[$j];
                }
                $ztmp3=$xtmp.$xtmp2;
            }


        if(!($dif&1)){
            $string=$ztmp.$string.$ztmp;
        }
        else{
            $string=$ztmp3.$string.$ztmp;
        }
    }



    return $string;
}
echo veloStrPad('Hello world',16, $padString='123456');

echo str_pad('Hello world', 16, '123456');
