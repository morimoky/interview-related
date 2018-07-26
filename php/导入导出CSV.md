#### 导出CSV
```
function export_csv($filename,$data)  
{  
    header("Content-type:text/csv");  
    header("Content-Disposition:attachment;filename=".$filename);  
    header('Cache-Control:must-revalidate,post-check=0,pre-check=0');  
    header('Expires:0');  
    header('Pragma:public');  
    echo $data;  
}
```
#### 导入CSV
```
function input_csv($handle)  
{  
    $out = array ();  
    $n = 0;  
    while ($data = fgetcsv($handle, 10000))  
    {  
        $num = count($data);  
        for ($i = 0; $i < $num; $i++)  
        {  
            $out[$n][$i] = $data[$i];  
        }  
        $n++;  
    }  
    return $out;  
} 
```
