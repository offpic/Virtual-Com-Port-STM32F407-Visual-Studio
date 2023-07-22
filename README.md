# Virtual-Com-Port-STM32F407-Visual-Studio
Virtual Com Port STM32F407 Visual Studio

https://www.youtube.com/watch?v=JQw2mjonNFY

![Screenshot_2](https://github.com/offpic/Virtual-Com-Port-STM32F404-Visual-Studio/assets/31142397/5e16a3c1-849d-4981-b6c9-eeb39a23074b)


# Visual-Studio Code

Imports System.IO.Ports
Public Class Form1
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        Windows.Forms.Control.CheckForIllegalCrossThreadCalls = False
        Try
            For Each port As String In SerialPort.GetPortNames()
                ComboBox1.Items.Add(port)
            Next

            ComboBox2.SelectedItem = "9600"
        Catch ex As Exception
            MsgBox(ex.Message)
        End Try

    End Sub

    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        If Button1.Text = "Connect" Then
            SerialPort1.BaudRate = Val(ComboBox2.SelectedItem)
            SerialPort1.PortName = ComboBox1.SelectedItem
            Try
                SerialPort1.Open()
                Button1.Text = "Disconnect"
                TextBox1.Enabled = True
                GroupBox1.Enabled = False
            Catch ex As Exception

            End Try
        Else
            SerialPort1.Close()
            TextBox1.Enabled = False
            GroupBox1.Enabled = True
            Button1.Text = "Connect"
        End If

    End Sub

    Private Sub TextBox1_KeyDown(sender As Object, e As KeyEventArgs) Handles TextBox1.KeyDown
        If e.KeyCode = Keys.Enter Then
            SerialPort1.Write(TextBox1.Text)
            TextBox1.Clear()
        End If
    End Sub

    Private Sub SerialPort1_DataReceived(sender As Object, e As SerialDataReceivedEventArgs) Handles SerialPort1.DataReceived
        RichTextBox1.Text &= SerialPort1.ReadExisting()
    End Sub

    Private Sub RichTextBox1_TextChanged(sender As Object, e As EventArgs) Handles RichTextBox1.TextChanged

    End Sub

    Private Sub ComboBox2_SelectedIndexChanged(sender As Object, e As EventArgs) Handles ComboBox2.SelectedIndexChanged

    End Sub

    Private Sub Button2_Click(sender As Object, e As EventArgs) Handles Button2.Click
        SerialPort1.Write("C")
    End Sub

    Private Sub Button3_Click(sender As Object, e As EventArgs) Handles Button3.Click
        SerialPort1.Write("c")
    End Sub

    Private Sub Button4_Click(sender As Object, e As EventArgs) Handles Button4.Click
        SerialPort1.Write("D")
    End Sub

    Private Sub Button5_Click(sender As Object, e As EventArgs) Handles Button5.Click
        SerialPort1.Write("d")
    End Sub

    Private Sub Button6_Click(sender As Object, e As EventArgs) Handles Button6.Click
        SerialPort1.Write("A")
    End Sub

    Private Sub Button7_Click(sender As Object, e As EventArgs) Handles Button7.Click
        SerialPort1.Write("a")
    End Sub

    Private Sub Button8_Click(sender As Object, e As EventArgs) Handles Button8.Click
        SerialPort1.Write("B")
    End Sub

    Private Sub Button9_Click(sender As Object, e As EventArgs) Handles Button9.Click
        SerialPort1.Write("b")
    End Sub
End Class

