# Desain dan Analisis Algoritma
Contoh penerapan Kompleksitas Algoritma menggunanakan bahasa  pemrograman PHP
1.	Selection Sort
Script :
<?php 
function selection_sort($data){
  for($i=0; $i<count($data)-1; $i++) {
    $min = $i;
    for($j=$i+1; $j<count($data); $j++) {
             if ($data[$j]<$data[$min]) {
                   $min = $j;
              }
     }
    $data = swap_positions($data, $i, $min);
   }
 return $data;
}

function swap_positions($data1, $left, $right) {
    $backup_old_data_right_value = $data1[$right];
    $data1[$right] = $data1[$left];
    $data1[$left] = $backup_old_data_right_value;
    return $data1;
}

$my_array = array(5, 1, 8, 16, 2, 12, 14);
echo "Inputan Array :\n";
echo implode(', ',$my_array );
?> <br>

<?php

echo "\nArray yang Sudah Diurut :\n";
echo implode(', ',selection_sort($my_array)). PHP_EOL;
?>
Hasil :
Inputan Array : 5, 1, 8, 16, 2, 12, 14
Array yang Sudah Diurut : 1, 2, 5, 8, 12, 14, 16

2.	Binary Search
Script :
<?php
  $val = 10;
  $arr_sort = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  $lower = 0;
  $upper = count($arr_sort) - 1;
  
  while($lower <= $upper)
  {
    if($arr_sort[($lower + $upper) / 2] == $val)
    {
      echo "Hasil pencarian binary search adalah " . $val;
      return;
    }
    else if ($arr_sort[($lower + $upper) / 2] < $val)
    {
      $lower = (int)(($lower + $upper) / 2 + 1);
    }
    else if ($arr_sort[($lower + $upper) / 2] > $val)
    {
      $upper = (int)(($lower + $upper) / 2 - 1);
    }
  }
  
  echo "Not found";
?>
Hasil :
Hasil pencarian binary search adalah 10

3.	Sequential Search
Script :
<?php

  function sequential_search(&$arr, $value)
  {
    $arr[] = $value;
    $index = 0;
   
    while ($arr[$index++] != $value);
   
    if ($index < count($arr)) {
      array_unshift($arr, $arr[$index-1]);
      unset($arr[$index]);
      unset($arr[count($arr)+1]);
   
      return true;
    }
   
    return false;
  }

  $arr = array(1, 2, 3, 3.14, 5, 4, 6, 9, 8);

  $x = 12;
   
  if (sequential_search($arr, $x)) {

    echo "Nilai yang diinput adalah 1,2,3,3.14,5,4,6,9,8 <br>";
    echo "Nilai yang dicari adalah $x <br>";
    echo "Nilai $x ditemukan!";
  } else {
    echo "Nilai yang diinput adalah 1,2,3,3.14,5,4,6,9,8 <br>";
    echo "Nilai yang dicari adalah $x <br>";
    echo "Nilai $x tidak ditemukan di dalam list! <br>";
  }
?>

Hasil :
Nilai yang diinput adalah 1,2,3,3.14,5,4,6,9,8
Nilai yang dicari adalah 12
Nilai 12 tidak ditemukan di dalam list!
