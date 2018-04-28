### <a name="accessibility-improvements-in-windows-forms-controls"></a>Windows フォーム コントロールでのアクセシビリティの向上

|   |   |
|---|---|
|説明|Windows フォームはアクセシビリティ テクノロジによってユーザー サポートの動作が向上します。 次のような点が変更されます。<ul><li>ハイ コントラスト モード中の表示が向上する変更。</li><li>プロパティ ブラウザーのエクスペリエンスが向上する変更。 プロパティ ブラウザーについては次のような点が向上します。</li><li>さまざまなドロップダウン選択ウィンドウを利用することでキーボード操作が便利になりました。</li><li>不要なタブ ストップが減ります。</li><li>コントロールの種類の報告機能が改善されました。</li><li>ナレーターの動作が改善されました。</li><li>コントロールに不足している UI アクセシビリティ パターンを実装する変更。</li></ul>|
|提案される解決策|<strong>以上の変更を選択する方法と選択しない方法</strong> アプリケーションでこれらの変更を利用するには、.NET Framework 4.7.1 以降で実行する必要があります。 アプリケーションは、次のいずれかの方法でこれらの変更を利用できます。<ul><li>.NET Framework 4.7.1 を対象にして再コンパイルします。 .NET Framework 4.7.1 以降を対象とする Windows フォーム アプリケーションでは、これらのアクセシビリティの変更が既定で有効になります。</li><li>下の例のように、app.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の [AppContext スイッチ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)を追加し、それを <code>false</code> に設定することで、以前のアクセシビリティ動作を無効にします。</li></ul><pre><code class="language-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET Framework 4.7.1 以降を対象とするアプリケーションで以前のアクセシビリティ動作を残す場合、この AppContext スイッチを明示的に <code>true</code> に設定することで以前のアクセシビリティ機能を選択できます。UI オートメーションの概要については、「[UI オートメーションの概要](~/docs/framework/ui-automation/ui-automation-overview.md)」をご覧ください。<strong>UI オートメーション パターンとプロパティに対して追加されたサポート</strong> アクセシビリティ クライアントは、一般的なパブリックに記述された呼び出しパターンを使って、新しい WinForms アクセシビリティ機能を利用できます。 これらのパターンは、WinForms に固有ではありません。 たとえば、アクセシビリティ クライアントは、IAccessible インターフェイス (MAAS) の QueryInterface メソッドを呼び出して、IServiceProvider インターフェイスを取得することができます。 このインターフェイスを使用できる場合、クライアントはその QueryService メソッドを使って、IAccessibleEx インターフェイスを要求できます。 詳しくは、「[Using IAccessibleEx from a Client](https://msdn.microsoft.com/library/windows/desktop/dd561924.aspx)」(クライアントからの IAccessibleEx の使用) をご覧ください。 .NET Framework 4.7.1、IServiceProvider で始まると[IAccessibleEx](https://msdn.microsoft.com/library/windows/desktop/dd561898.aspx) (該当する場合) が WinForms ユーザー補助オブジェクトに対して使用します。 .NET Framework 4.7.1 は、次の UI オートメーション パターンやプロパティのサポートを追加します。<ul><li><code>T:System.Windows.Forms.ToolStripSplitButton</code> および <code>T:System.Windows.Forms.ComboBox</code> コントロールは、[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)をサポートします。</li><li><code>T:System.Windows.Forms.ToolStripMenuItem</code> コントロールの [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値は <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> です。</li><li><code>T:System.Windows.Forms.ToolStripItem</code> コントロールは、[Name](xref:System.Windows.Automation.AutomationElement.NameProperty) プロパティと[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)をサポートします。</li><li><code>T:System.Windows.Forms.ToolStripDropDownItem</code> コントロールは、ドロップダウンが展開されたり折りたたまれたりしたときの StateChange と NameChange を示す <xref:System.Windows.Forms.AccessibleEvents> をサポートします。</li><li><code>T:System.Windows.Forms.ToolStripDropDownButton</code> コントロールの [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値は <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> です。</li><li><code>T:System.Windows.Forms.DataGridViewCheckBoxCell</code> コントロールは[トグル パターン](xref:System.Windows.Automation.TogglePattern)をサポートします。</li><li><code>T:System.Windows.Forms.NumericUpDown</code> および <code>T:System.Windows.Forms.DomainUpDown</code> コントロールは、[Name](xref:System.Windows.Automation.AutomationElement.NameProperty) をサポートし、[ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md) は <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType> です。</li></ul><strong>PropertyGrid コントロールの向上</strong> .NET Framework 4.7.1 では、PropertyBrowser コントロールが次のように向上します。<ul><li>ユーザーが <code>T:System.Windows.Forms.PropertyGrid</code> コントロールに誤った値を入力すると表示されるエラー ダイアログの <strong>[詳細]</strong> ボタンは、[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)、状態と名前の変更通知、および [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値 <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType> をサポートします。</li><li>エラー ダイアログの <strong>[詳細]</strong> ボタンを展開すると表示されるメッセージ ウィンドウは、キーボードでアクセスできるようになり、エラー メッセージの内容をナレーターで読み上げることができます。</li><li><code>T:System.Windows.Forms.PropertyGrid</code> コントロールの行の <xref:System.Windows.Forms.AccessibleRole> は、&quot;Row&quot; から &quot;Cell&quot; に変更されました。 セルは UIA の ControlType &quot;DataItem&quot; にマップし、適切なキーボード ショートカットとナレーターの読み上げをサポートすることができます。</li><li><code>T:System.Windows.Forms.PropertyGrid</code> コントロールの <code>P:System.Windows.Forms.PropertySort</code> プロパティが <code>F:System.Windows.Forms.PropertySory.Categorized</code> に設定されているときにヘッダー項目を表す <code>T:System.Windows.Forms.PropertyGrid</code> コントロールの行は、[ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) プロパティの値が <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType> です。</li><li><code>T:System.Windows.Forms.PropertyGrid</code> コントロールの <code>P:System.Windows.Forms.PropertySort</code> プロパティが <code>F:System.Windows.Forms.PropertySory.Categorized</code> に設定されているときにヘッダー項目を表す <code>T:System.Windows.Forms.PropertyGrid</code> コントロールの行は、[展開/折りたたみパターン](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)をサポートします。</li><li>グリッドとその上にある ToolBar の間のキーボード ナビゲーションが向上します。 &quot;Shift + Tab&quot; キーを押すと、ToolBar 全体ではなく、ToolBar の最初のボタンが選択されます。</li><li>ハイ コントラスト モードで表示された <code>T:System.Windows.Forms.PropertyGrid</code> コントロールでは、<code>P:System.Windows.Forms.PropertySort</code> プロパティの現在の値に対応する ToolBar ボタンの周囲にフォーカス四角形が描画されます。</li><li>ハイ コントラスト モードで表示され、<code>P:System.Windows.Forms.PropertySort</code> プロパティが <code>F:System.Windows.Forms.PropertySory.Categorized</code> に設定された <code>T:System.Windows.Forms.PropertyGrid</code> コントロールでは、カテゴリ ヘッダーの背景がハイ コントラストの色で表示されます。</li><li><code>T:System.Windows.Forms.PropertyGrid</code> コントロールでは、フォーカスが設定された ToolBar 項目と、<code>P:System.Windows.Forms.PropertySort</code> プロパティの現在の値を示す ToolBar 項目の区別が明確になります。 この修正は、ハイ コントラストの変更と、非ハイ コントラストのシナリオに対する変更で構成されます。</li><li><code>P:System.Windows.Forms.PropertySort</code> プロパティの現在の値を示す <code>T:System.Windows.Forms.PropertyGrid</code> コントロールの ToolBar 項目は、[トグル パターン](xref:System.Windows.Automation.TogglePattern)をサポートします。</li><li>配置ピッカーで選択された配置を区別するナレーターのサポートが向上します。</li><li>空の <code>T:System.Windows.Forms.PropertyGrid</code> コントロールがフォームに表示されているとき、以前はフォーカスを設定されませんでしたが、現在はフォーカスを設定されるようになっています。</li></ul><strong>ハイ コントラスト テーマでの OS で定義された色の使用</strong><ul><li><code>P:System.Windows.Forms.Control.FlatStyle</code> が <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType> (既定のスタイル) に設定された <code>T:System.Windows.Forms.Button</code> および <code>T:System.Windows.Forms.CheckBox</code> コントロールは、ハイ コントラスト テーマが選択されているときは OS で定義された色を使用するようになります。 以前は、テキストと背景の色はコントラストが同じで、見分けるのが困難でした。</li><li><code>P:System.Windows.Forms.Control.Enabled</code> が <em>false</em> に設定された <code>T:System.Windows.Forms.Button</code>、<code>T:System.Windows.Forms.CheckBox</code>、<code>T:System.Windows.Forms.RadioButton</code>、<code>T:System.Windows.Forms.Label</code>、<code>T:System.Windows.Forms.LinkLabel</code>、および <code>T:System.Windows.Forms.GroupBox</code> は、以前は影付きの色を使ってハイ コントラスト テーマのテキストをレンダリングしており、背景に対するコントラストが低くなっていました。 現在は、これらのコントロールは OS によって定義された &quot;無効なテキスト&quot; の色を使うようになっています。 この修正は、<code>P:System.Windows.Forms.Control.FlatStyle</code> プロパティが <code>F:System.Windows.Forms.FlatStyle.System</code> 以外の値に設定されたコントロールに適用されます。 後者のコントロールは OS によってレンダリングされます。</li><li><code>T:System.Windows.Forms.DataGridView</code> では、現在フォーカスが設定されているセルの内容を囲むように目に見える四角形がレンダリングされます。 以前は、特定のハイ コントラスト テーマではこれは見えませんでした。</li><li><code>P:System.Windows.Forms.ToolStripItem.Enabled</code> プロパティが <em>false</em> に設定された <code>T:System.Windows.Forms.ToolStripMenuItem</code> コントロールは、OS によって定義された &quot;無効なテキスト&quot; の色を使うようになります。</li><li><code>P:System.Windows.Forms.ToolStripItem.Checked</code> プロパティが <em>true</em> に設定された <code>T:System.Windows.Forms.ToolStripMenuItem</code> コントロールは、コントラストのあるシステム カラーで関連するチェック マークをレンダリングします。  以前は、チェック マークの色に十分なコントラストがなく、ハイ コントラスト テーマでは見えませんでした。</li></ul>注: Windows 10 では、一部のハイ コントラストのシステム カラーの値が変更されています。 Windows フォームのフレームワークは、Win32 フレームワークに基づいています。 最も快適に利用するためには、最新版の Windows で実行し、テスト アプリケーションに app.manifest ファイルを追加して最新の OS 変更を選択し、次のコードのコメントを解除します。<pre><code>&lt;!-- Windows 10 --&gt;&#13;&#10;&lt;supportedOS Id=&quot;{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}&quot; /&gt;&#13;&#10;</code></pre><strong>キーボード ナビゲーションの向上</strong><ul><li><code>T:System.Windows.Forms.ComboBox</code> コントロールの <code>P:System.Windows.Forms.ComboBox.DropDownStyle</code> が <code>F:System.Windows.Forms.DropDownStyle.DropDownList</code> に設定されていて、フォームのタブ オーダーで最初のコントロールである場合、キーボードを使って親フォームが開かれると、コントロールにフォーカスの四角形が表示されます。 この変更の前は、キーボード フォーカスはこのコントロールに設定されましたが、フォーカス インジケーターはレンダリングされませんでした。</li></ul><strong>ナレーター サポートが改善されました</strong><ul><li><code>T:System.Windows.Forms.MonthCalendar</code> コントロールに、以前は行われなかったナレーターによるコントロールの値の読み上げなど、コントロールにアクセスするための支援技術のサポートが追加されました。</li><li><code>T:System.Windows.Forms.CheckedListBox</code> コントロールは、<code>P:System.Windows.Forms.CheckState</code> プロパティが変更されるとナレーターに通知するようになりました。 以前は、ナレーターは通知を受け取らなかったため、ユーザーは <code>P:System.Windows.Forms.CheckState</code> が更新されたことを教えられませんでした。</li><li><code>T:System.Windows.Forms.LinkLabel</code> コントロールがコントロール内のテキストをナレーターに通知する方法が変更されました。 以前は、ナレーターはこのテキストを 2 回読み上げ、ユーザーには表示されなくても &quot;&amp;&quot; 記号を実際のテキストとして読んでいました。 重複するテキストおよび不要な &quot;&amp;&quot; 記号が、ナレーターの読み上げから除去されました。</li><li><code>T:System.Windows.Forms.DataGridViewCell</code> コントロールの種類が、読み取り専用の状態をナレーターおよびその他の支援技術に正しくレポートするようになりました。</li><li>ナレーターは、[マルチドキュメント インターフェイス](~/docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md) アプリケーションの子ウィンドウのシステム メニューを読み上げられるようになりました。</li><li>ナレーターは、<code>P:System.Windows.Forms.ToolStripItem.Enabled</code> プロパティが <em>false</em> に設定された <code>T:System.Windows.Forms.ToolStripMenuItem</code> コントロールを読み上げられるようになりました。 以前のナレーターは、無効なメニュー項目にフォーカスを設定できず、内容を読み上げることができませんでした。</li></ul>|
|スコープ|Major|
|Version|4.7.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType></li><li>[MonthCalendar.AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)</li></ul>|
