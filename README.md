<?php
class Calculator {
    public static function calculate($num1, $num2, $operator) {
        switch ($operator) {
            case '+': return $num1 + $num2;
            case '-': return $num1 - $num2;
            case '*': return $num1 * $num2;
            case '/': return $num2 != 0 ? $num1 / $num2 : "Error: Division by zero";
            default: return "Invalid operator";
        }
    }
}

$result = "";
if ($_SERVER["REQUEST_METHOD"] === "POST") {
    $num1 = floatval($_POST['num1']);
    $num2 = floatval($_POST['num2']);
    $operator = $_POST['operator'];
    $result = Calculator::calculate($num1, $num2, $operator);
}
?>

<!DOCTYPE html>
<html>
<head>
    <title>Professional PHP Calculator</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 50px; }
        input, select, button { padding: 10px; margin: 5px; }
    </style>
</head>
<body>
    <h2>Professional Calculator</h2>
    <form method="post">
        <input type="number" step="any" name="num1" required>
        <select name="operator">
            <option>+</option>
            <option>-</option>
            <option>*</option>
            <option>/</option>
        </select>
        <input type="number" step="any" name="num2" required>
        <button type="submit">Calculate</button>
    </form>
    <?php if($result !== ""): ?>
        <h3>Result: <?= htmlspecialchars($result) ?></h3>
    <?php endif; ?>
</body>
</html>
