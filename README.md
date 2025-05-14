// PenghuniController.php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use App\Models\Penghuni;

class PenghuniController extends Controller
{
    public function index()
    {
        $penghuni = Penghuni::all();
        return view('penghuni.index', compact('penghuni'));
    }

    public function create()
    {
        return view('penghuni.create');
    }

    public function store(Request $request)
    {
        Penghuni::create($request->all());
        return redirect()->route('penghuni.index');
    }

    public function edit($id)
    {
        $penghuni = Penghuni::find($id);
        return view('penghuni.edit', compact('penghuni'));
    }

    public function update(Request $request, $id)
    {
        Penghuni::find($id)->update($request->all());
        return redirect()->route('penghuni.index');
    }

    public function destroy($id)
    {
        Penghuni::find($id)->delete();
        return redirect()->route('penghuni.index');
    }
}

